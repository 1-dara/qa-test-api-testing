# Test Plan: ReqRes API (reqres.in)

**Project:** QA Portfolio – Project 2 (API Testing)
**Tester:** Irene Peter-Okon
**Date:** 07-07-2026
**API Under Test:** https://reqres.in/api

## Scope
GET, POST, PUT, DELETE requests against the /users and /register endpoints, covering status codes, response schema, and error handling.

## Test Cases

### GET Requests

**TC-API-001: Get list of users (valid page)**
- Request: GET /api/users?page=2
- Expected: 200 status, response contains `data` array, each user has id/email/first_name/last_name

**TC-API-002: Get single user (valid ID)**
- Request: GET /api/users/2
- Expected: 200 status, response contains single user object matching ID requested

**TC-API-003: Get single user (invalid/non-existent ID)**
- Request: GET /api/users/9999
- Expected: 404 status, empty response body

**TC-API-004: Get list of users (invalid page number)**
- Request: GET /api/users?page=9999
- Expected: 200 status, `data` array is empty

### POST Requests

**TC-API-005: Create a new user (valid data)**
- Request: POST /api/users with { name, job }
- Expected: 201 status, response echoes name/job, includes generated id and createdAt

**TC-API-006: Register user (valid email + password)**
- Request: POST /api/register with valid email/password
- Expected: 200 status, response contains id and token

**TC-API-007: Register user (missing password)**
- Request: POST /api/register with only email
- Expected: 400 status, error message: "Missing password"

### PUT Requests

**TC-API-008: Update existing user**
- Request: PUT /api/users/2 with { name, job }
- Expected: 200 status, response echoes updated name/job, includes updatedAt

### DELETE Requests

**TC-API-009: Delete existing user**
- Request: DELETE /api/users/2
- Expected: 204 status, empty response body

## Summary
- Total test cases: 9
- Passed: 8
- Failed: 1
