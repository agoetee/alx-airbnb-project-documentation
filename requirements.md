# Requirement Specifications for Backend Features 

Write detailed requirement specifications for at least three key backend features from Task 1 (e.g., User 
Authentication, Property Management, Booking System).

## 1. User Authentication
### Requirement Specifications
__User Registration__
    - The system shall allow users to register using a valid email and a password.
    - The system shall validate that the email address is unique
__User Login__
    - The system shall allow users to login using their
    - The system shall verify the credentials and return an authentication token
### API endpoints
- `/register`
- `/login`
- `/token refresh`

### Input/Output Specifications

|Input        |Output    |
|-------------|----------|
|`first_name` |HTTP 201  |
|`last_name`  |HTTP 400  |
|`email`      |JSON      |

### Validation Rules

First Name/ Last Name
- Required
- Length between 2 and 50 characters
- No digits allowed

### Performance Criteria
- Availability:
    - System should have 99.9% uptime or better
    - Authentication endpoints must be available through peak usage times
- Scalability:
    - The Authentication service should support __horizontal__ scaling eg. load balanced servers
    - Should maintain performance with increased user base


## 2. Property Management
### Requirement Specification
__Add Listing__
- The system allows a host with to add a property into the system
- The Host enters the details of the property to add it.
__Edit Listing__
- When new features are added to the property, the guest can update it.
- Likewise when some features are no longer available, they can update it
__Delete Listing__
- The Host can delete a listing when It is no longer on offer.

### API endpoints
- `/property_add`
- `/property_update`
- `/property_delete`

### Input/Output Specifications
|Input          |Output                     |
|---------------|---------------------------|
|`property_name`  |HTTP 201                   |
|`description`    |HTTP 400                   |
|`location`       |Property details (echo)    |
|`price_per_night`|                           |
|`amenities`      |                           |

### Validation Rules
__Property Name__
- Required
- minimum characters (2)
- Maximum characters (50)

## 3. Booking System

### Requirement Specification
__Booking Creation__
- Allows a User to select a property and create a booking
- User can select from many properties according to price and location

__Booking Cancellation__
- A Guest can cancel a booking when plans change
- A Host can cancel booking of a Guest

__Booking Status__
- Guest can see the different status of booking ie: booked, confirmed, etc
- Host can check the status of a booking.

### API endpoints
- `/booking_create`
- `/booking_status`
- `/booking_cancel`

### Input/Output Specifications
|Input              |Output                     |
|-------------------|---------------------------|
|`booking_date`     |HTTP 201                   |
|`property`         |HTTP 400                   |
|`no_of_days`       |Booking Details            |
|`amount`           |                           |

### Validation Rules
- Booking date cannot be in the past
- Cannot book multiple properties on same day