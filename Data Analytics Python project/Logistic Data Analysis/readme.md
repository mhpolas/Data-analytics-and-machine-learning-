## GlobalExpress - Delivery Efficiency AnalysisBackground

GlobalExpress Logistics is a package delivery company that operates across multiple zones with different warehouses and drivers. The company has been collecting data on their operations but has not been able to effectively analyze it to improve efficiency and profitability.

My task is to analyze the provided datasests, derive meaningful insights, and suggest improvements to the company's operations.

## Dataset Description

The dataset consists of four CSV files:

1. **data_deliveries.csv**: Main transactional data about package deliveries
2. **data_drivers.csv**: Information about delivery drivers
3. **data_warehouses.csv**: Details about company warehouses
4. **data_zones.csv**: Information about delivery zones

### Complete Data Dictionary

#### data_deliveries.csv (Main Transaction Data)

**Package Information:**
- `package_id`: Unique identifier for each package (UUID format)
- `package_type`: Type of package (Standard, Express, Same-day, Fragile, Heavy, Refrigerated)
- `package_weight`: Weight of the package in kg
- `package_width`: Width of the package in cm
- `package_height`: Height of the package in cm
- `package_depth`: Depth of the package in cm
- `package_value`: Declared value of the package in USD
- `package_insurance`: Boolean indicating if the package is insured

**Delivery Details:**
- `date`: Date of delivery
- `time_of_day`: Time when the delivery was initiated (HH:MM format)
- `driver_id`: ID of the driver who delivered the package
- `warehouse_id`: ID of the warehouse from which the package originated
- `delivery_zone_id`: ID of the zone where the package was delivered
- `vehicle_type`: Type of vehicle used (Van, Truck, Motorcycle, Bicycle)
- `is_return_trip`: Boolean indicating if this was a return delivery

**Delivery Performance:**
- `promised_delivery_time`: Time promised to the customer (in hours from order)
- `actual_delivery_time`: Actual time taken for delivery (in hours)
- `delivery_status`: Status (On Time, Slightly Delayed, Significantly Delayed)
- `customer_rating`: Rating given by the customer (1-5 scale, with 0.5 increments)

**Environmental Factors:**
- `weather_condition`: Weather during delivery (Clear, Cloudy, Rainy, Stormy, Snowy, Foggy, Windy)
- `traffic_condition`: Traffic conditions (Light, Moderate, Heavy, Severe)
- `fuel_consumption`: Amount of fuel consumed for the delivery (in liters)

**Business Metrics:**
- `delivery_cost`: Total cost of delivering the package (USD)
- `profitability`: Profit generated from the delivery (USD)
- `optimization_factor`: Internal metric for delivery optimization (0-1 scale)

**Customer Information:**
- `customer_id`: Unique identifier for the customer
- `payment_method`: Method of payment (Credit Card, Cash, PayPal, Invoice)
- `promotional_code_used`: Boolean indicating if a promo code was used
- `is_new_customer`: Boolean indicating if this is a new customer
- `has_mobile_notification`: Boolean indicating if mobile notifications were enabled

#### data_drivers.csv (Driver Information)

**Basic Information:**
- `driver_id`: Unique identifier for each driver
- `driver_name`: Name of the driver
- `license_number`: Driver's license number
- `driver_rating`: Average rating of the driver (1-5 scale)
- `years_experience`: Years of driving experience

**Work Details:**
- `vehicle_type`: Type of vehicle the driver typically uses
- `home_warehouse`: Driver's assigned warehouse
- `shift_preference`: Preferred shift (Morning, Afternoon, Evening, Night)
- `max_packages_per_day`: Maximum packages the driver can deliver per day
- `has_refrigeration_unit`: Boolean indicating if driver's vehicle has refrigeration

**Employment Information:**
- `last_training_date`: Date of the driver's last training
- `salary_tier`: Salary level (1-4)
- `bonus_eligible`: Boolean indicating bonus eligibility

#### data_warehouses.csv (Warehouse Information)

**Basic Information:**
- `warehouse_id`: Unique identifier for each warehouse
- `warehouse_name`: Name of the warehouse
- `capacity`: Total storage capacity
- `location_latitude`: Geographical latitude
- `location_longitude`: Geographical longitude

**Operational Details:**
- `operating_hours`: Daily operating hours (format: HH:MM-HH:MM)
- `manager_id`: ID of the warehouse manager
- `refrigeration_capacity`: Capacity for refrigerated storage
- `has_automated_sorting`: Boolean indicating presence of automated sorting
- `maintenance_schedule`: Frequency of maintenance (Weekly, Bi-weekly, Monthly)
- `electricity_cost`: Monthly electricity cost in USD

#### data_zones.csv (Delivery Zone Information)

**Basic Information:**
- `zone_id`: Unique identifier for each delivery zone
- `zone_name`: Name of the zone
- `distance_from_hub`: Distance from the central hub in km
- `population`: Population in the zone
- `avg_income`: Average income of residents in USD

**Zone Characteristics:**
- `urban_density`: Density classification (High, Medium, Low)
- `primary_warehouse`: ID of the primary serving warehouse
- `zone_type`: Type of zone (Residential, Commercial, Industrial, Mixed)
- `avg_delivery_time`: Average delivery time in hours
- `parking_difficulty`: Parking difficulty rating (1-5 scale)
- `zone_growth_rate`: Annual growth rate of delivery volume

## Business Questions

The COO has put you in charge to investigate and recommend strategies to improve delivery performance.

More specifically, the following questions must be answered:

- What factors have the strongest influence on delivery times?
- How do weather and traffic conditions affect delivery performance?
- Are there specific delivery zones with consistently poor performance?

