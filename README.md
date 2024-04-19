# ECommerce API Documentation

## Overview

This documentation provides detailed information about the ECommerce API, which is a CRUD API for managing products of an ECommerce shopping website. The API is built using Python, Django, Django Rest Framework, and MySQL, and is deployed on PythonAnywhere.

## Table of Contents

1. [Introduction](#introduction)
2. [Endpoints](#endpoints)
3. [Authentication](#authentication)
4. [Request and Response Formats](#request-and-response-formats)
5. [Models](#models)
6. [Views](#views)
7. [Serializers](#serializers)
8. [Deployment](#deployment)
9. [Testing](#testing)
10. [Future Enhancements](#future-enhancements)

## Introduction

The ECommerce API provides CRUD (Create, Read, Update, Delete) functionality for managing products of an ECommerce shopping website. It allows users to perform operations such as creating new products, retrieving product details, updating existing products, and deleting products.

## Endpoints

The following endpoints are available in the API:

- **GET /products/**: Retrieve a list of all products.
- **POST /products/**: Create a new product.
- **GET /products/{id}/**: Retrieve details of a specific product.
- **PUT /products/{id}/**: Update details of a specific product.
- **DELETE /products/{id}/**: Delete a specific product.

## Authentication

Authentication is not required to access the API endpoints.

## Request and Response Formats

All requests and responses are in JSON format.

### Request Format

For POST and PUT requests, the request body should contain JSON data representing the product attributes.

Example:
```json
{
    "name": "Product Name",
    "description": "Product Description",
    "price": 29.99
}
```

### Response Format

Responses for successful requests include JSON data representing the product attributes. For list endpoints, the response is a JSON array containing multiple product objects.

Example:
```json
{
    "id": 1,
    "name": "Product Name",
    "description": "Product Description",
    "price": 29.99
}
```

## Models

The API uses the following Django model to represent products:

```python
from django.db import models

class Product(models.Model):
    name = models.CharField(max_length=100)
    description = models.TextField()
    price = models.DecimalField(max_digits=10, decimal_places=2)

    def __str__(self):
        return self.name
```

The `Product` model stores information about each product, including its name, description, and price.

## Views

The API utilizes Django Rest Framework's generic views to handle CRUD operations for products. The views are mapped to the respective endpoints as described in the Endpoints section.

## Serializers

Serializers are used to convert model instances to JSON format and vice versa. The following serializer is used for the Product model:

```python
from rest_framework import serializers
from .models import Product

class ProductSerializer(serializers.ModelSerializer):
    class Meta:
        model = Product
        fields = '__all__'
```

## Deployment

The API is deployed on PythonAnywhere, a cloud platform for hosting Python applications. Deployment involves configuring a WSGI file and setting up the necessary environment variables.

## Testing

Testing of the API can be performed using tools such as Django's built-in test framework, Postman, or curl commands. Unit tests should cover all endpoints and functionalities to ensure proper behavior.

## Future Enhancements

Future enhancements to the API may include:

- Implementing authentication and authorization mechanisms.
- Adding pagination support for list endpoints.
- Enabling filtering, sorting, and searching capabilities.
- Integrating caching mechanisms for improved performance.
- Enhancing documentation with examples and usage guidelines.
