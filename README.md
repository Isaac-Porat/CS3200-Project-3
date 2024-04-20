# Redis Commands for Sneaker Shoe Inventory Sourcing System

This README outlines the Redis commands used in the Sneaker Shoe Inventory Sourcing System for various functionalities including storing and accessing reseller’s search criteria, managing user sessions, and queuing scraping tasks.

## Storing and Accessing Reseller’s Search Criteria

### Create
To create or update a reseller's search criteria:
- HSET search_criteria:123 shoe_name "Air Force 1" size "10" price_range "100-200" zip_code "12345" quality_indicator "80-100"

### Retrieve
To retrieve a reseller's search criteria:
- HGETALL search_criteria:123

### Update
To update a specific field in a reseller's search criteria (e.g., price range):
- HSET search_criteria:123 price_range "150-250"

### Delete
To delete a reseller's search criteria:
- DEL search_criteria:123

## Managing User Sessions

### Create
To create a user session and set an expiration time (e.g., 1 hour):
- HSET session:abc123 user_id "123" last_access "2023-09-21T14:00:00Z" preferences "{...}"
EXPIRE session:abc123 3600

### Retrieve
To retrieve all data for a user session:
- HGETALL session:abc123
  
### Update
To update a specific field in a user session (e.g., last access time):
- HSET session:abc123 last_access "2023-09-21T15:00:00Z"

### Delete
To delete a user session:
- DEL session:abc123

## Queuing Scraping Tasks

### Create
To add a new scraping task to the queue:
- LPUSH scraping_tasks_queue '{"search_criteria": {...}, "task_id": "xyz123"}'
