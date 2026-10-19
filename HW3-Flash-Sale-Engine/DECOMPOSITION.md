
# HW3 — Flash Sale Engine Decomposition

## 1. Project Overview

The Flash Sale Engine application simulates a flash sale in which products
can be purchased while the sale is active and stock is available.

The system is decomposed into the user interface, product presentation,
sale lifecycle management, purchase processing, inventory management,
and application state.

## 2. Decomposition Tree

```text
Flash Sale Engine
|
+-- 1. User Interface
|   +-- Display sale information
|   +-- Display product cards
|   +-- Display prices and stock
|   +-- Provide purchase controls
|
+-- 2. Product Management
|   +-- Store product information
|   +-- Provide product data to the interface
|   +-- Track available stock
|
+-- 3. Sale Lifecycle
|   +-- Start the sale
|   +-- Track sale status
|   +-- End the sale
|   +-- Handle countdown-related updates
|
+-- 4. Purchase Processing
|   +-- Receive purchase requests
|   +-- Validate sale and stock conditions
|   +-- Update inventory after successful purchases
|   +-- Return purchase results
|
+-- 5. State Management
|   +-- Maintain sale state
|   +-- Maintain product and inventory state
|   +-- Update the interface after state changes
|
+-- 6. Styling and Feedback
    +-- Arrange the sale interface
    +-- Highlight sale information
    +-- Display purchase and stock status
```

## 3. Module Specifications

### 3.1 User Interface

**Purpose:** Present sale information and allow users to interact with products.

**Input:** Product data, sale state, inventory information, and user actions.

**Processing:**
- Render product information and purchase controls.
- Display current stock and sale status.
- Refresh the interface after relevant state changes.

**Output:** An interactive flash sale interface.

### 3.2 Product Management

**Purpose:** Maintain product information used by the sale.

**Input:** The product data defined by the application.

**Processing:**
- Store product details.
- Provide product information to the interface.
- Maintain available inventory through the sale engine.

**Output:** Product information and current stock values.

### 3.3 Sale Lifecycle

**Purpose:** Control whether the flash sale is active.

**Input:** Sale-start and sale-end actions, together with relevant timing events.

**Processing:**
- Start the sale.
- Track the current sale state.
- End the sale when the applicable condition is reached.
- Coordinate countdown-related behavior with the interface.

**Output:** The current sale status.

### 3.4 Purchase Processing

**Purpose:** Process product purchases during the sale.

**Input:** A product identifier and the current sale and inventory state.

**Processing:**
- Check whether the sale permits purchases.
- Check whether the requested product has available stock.
- Update stock after a successful purchase.
- Return a result that the interface can display.

**Output:** A purchase result and updated inventory state.

### 3.5 State Management

**Purpose:** Keep sale and inventory information consistent within the running application.

**Input:** Sale lifecycle events and purchase requests.

**Processing:**
- Maintain the current sale state.
- Maintain product stock values.
- Make state changes available to the rendering logic.

**Output:** Updated application state.

### 3.6 Styling and Feedback

**Purpose:** Make sale information and user actions easy to understand.

**Input:** Application content and interaction states.

**Processing:**
- Apply the visual layout and styling.
- Emphasize important sale information.
- Present stock and purchase feedback through the interface.

**Output:** A styled interface with visible interaction feedback.

## 4. Main Processing Flow

1. The application loads product data.
2. The interface renders the products and their stock.
3. The sale starts and its state is updated.
4. The user selects a product to purchase.
5. The sale engine checks the sale state and product availability.
6. If the purchase is valid, the available stock is reduced.
7. The interface renders the updated stock and purchase result.
8. The sale ends when the applicable end condition is reached.

## 5. Dependencies Between Modules

- The User Interface displays data supplied by the application state.
- Product Management provides product information and inventory values.
- Sale Lifecycle determines whether purchasing is permitted.
- Purchase Processing uses sale state and inventory information.
- State Management coordinates updates after purchases and lifecycle events.
- Styling and Feedback controls the presentation of the interface.

## 6. Testing Considerations

- Verify that product information is displayed correctly.
- Verify that purchases are accepted only when permitted by the sale state.
- Verify that stock decreases after a successful purchase.
- Verify that a product cannot be purchased when its stock is exhausted.
- Verify that the sale can be ended.
- Verify that the interface reflects inventory and sale-state changes.
- Verify relevant boundary conditions and invalid purchase requests.

## 7. Scope and Implementation Notes

This project simulates flash sale behavior in the client application.

The decomposition describes the logical responsibilities of the system.
The actual source code determines which validations and state transitions are implemented.

Because this is a client-side simulation, it does not by itself guarantee
inventory consistency across multiple users or concurrent purchases.
A real multi-user flash sale would require suitable backend validation
and reliable inventory updates.
```

5. Nhấn **Ctrl + S** để lưu.

Khi xong, nhắn **“xong HW3”**. Sau đó mình sẽ hướng dẫn kiểm tra đủ cả 3 file rồi **commit và push từng phần lên GitHub**, không gom tất cả thành một lần.