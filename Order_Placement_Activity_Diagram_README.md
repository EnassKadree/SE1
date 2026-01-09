# Order Placement Activity Diagram

This file contains an activity diagram for the order placement process, covering both happy path scenarios and error flows.

## File Format

The diagram is created in **PlantUML** format (`.puml` file), which is a widely-used text-based diagramming language.

## How to View the Diagram

### Option 1: Online Viewer (Easiest)
1. Go to http://www.plantuml.com/plantuml/uml/
2. Copy the contents of `Order_Placement_Activity_Diagram.puml`
3. Paste into the online editor
4. The diagram will render automatically

### Option 2: VS Code Extension
1. Install "PlantUML" extension in VS Code
2. Open the `.puml` file
3. Press `Alt+D` (or right-click and select "Preview PlantUML")

### Option 3: Command Line (requires Java)
```bash
# Install PlantUML (requires Java)
# On macOS: brew install plantuml
# Then render:
plantuml Order_Placement_Activity_Diagram.puml
```

### Option 4: IntelliJ IDEA / Other IDEs
- Most modern IDEs have PlantUML plugins available

## Diagram Overview

The activity diagram covers:

### Happy Path Flow:
1. User authentication check
2. Cart validation
3. Inventory availability check
4. Delivery address and province selection
5. Delivery fee calculation
6. Payment information entry and validation
7. OTP generation and sending
8. OTP verification
9. Order creation and inventory update
10. Order confirmation

### Error Flows Handled:
- **Authentication errors**: Redirect to login
- **Empty cart**: Show message and redirect
- **Out of stock items**: Remove items or update quantities
- **Invalid payment info**: Show validation errors with retry
- **OTP expiration**: Resend new OTP
- **Invalid OTP**: Allow retries (max 3 attempts)
- **Maximum attempts exceeded**: Cancel order process

## Key Features

- **Partitioned sections** for better organization:
  - Order Review & Validation
  - Payment Information
  - OTP Verification
  - Order Creation

- **Decision points** for all error scenarios
- **Error handling** with appropriate user feedback
- **Retry mechanisms** for OTP and payment validation
- **Inventory management** integrated into the flow

## Integration with Requirements

This diagram implements:
- **FR-CA-010**: Order Placement
- **FR-CA-007**: Order Verification (OTP)
- **FR-CA-008**: Shopping Cart Functionality
- **FR-CA-009**: Cart Review Page
- **FR-AD-011**: Automatic Inventory Updates



