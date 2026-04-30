# Service Toolkit for D365 Customer Service

Custom entities and web resources that extend the D365 Customer Service Workspace with manufacturing-specific service capabilities.

## What's Included

### Custom Entities
| Entity | Description |
|--------|-------------|
| **Warranty Claim** (`cr74e_warrantyclaim`) | Track warranty claims with product, serial, status |
| **Credit Memo and RMA** (`cra1f_creditmemoandrma`) | Return merchandise authorization + credit processing |
| **Parts** (`cr74e_parts`) | Parts catalog linked to products |
| **Product Serial** (`cr74e_productserial`) | Serial number tracking with warranty linkage |
| **Customer Order** (`trn_customerorder`) | Order tracking for the service context |
| **Claim Status** (`cr74e_claimstatus`) | Claim status tracking |
| **Root Cause** (`cr74e_rootcause`) | Root cause analysis codes |
| **Customer Interaction** (`cr74e_customerinteraction`) | Interaction history |
| **Department** (`cr74e_department`) | Department routing |

### Web Resources
| Resource | Description |
|----------|-------------|
| **Service Toolkit Loader** (`bw_ServiceToolkitLoader`) | Sideloader HTML for the CS Workspace productivity pane — renders custom panels (orders, warranty, RMA) alongside the case form |
| **BI RMA Dashboard** (`cra1f_bi_rma`) | RMA analytics dashboard |

## Installation

### Option A: Import the solution
1. Download `solution/ServiceToolkit_1_0_0_0_clean.zip`
2. Go to **make.powerapps.com** → Solutions → Import
3. Upload the ZIP → Import

### Option B: PAC CLI
```bash
pac auth create --url https://your-org.crm.dynamics.com
pac solution import --path solution/ServiceToolkit_1_0_0_0_clean.zip --activate-plugins --publish-changes
```

## Dependencies

The **clean** solution requires only:
- **D365 Customer Service** (`msdynce_Service`) — for `incident` entity
- **Product Management** (`msdynce_ProductManagement`) — for `product`, `pricelevel` entities
- **Enhanced Case Experience** (`msdyn_ModernCaseManagement`) — for attachment controls

These are standard with any D365 Customer Service or Sales license.

## Solution Variants

| File | Size | Dependencies | Notes |
|------|------|-------------|-------|
| `ServiceToolkit_1_0_0_0_clean.zip` | 116 KB | Service + Product Mgmt only | **Recommended** for customer delivery |
| `ServiceToolkit_1_0_0_0.zip` | 4.3 MB | 8 managed solutions | Full version with Canvas App (requires Field Service, Marketing) |

## Adding the Service Toolkit to CS Workspace

1. Open **Customer Service admin center**
2. Navigate to **Workspaces** → **Agent Experience Profiles**
3. Select your profile → **Productivity Pane** → enable
4. Add `bw_ServiceToolkitLoader` as a custom productivity tool
5. The toolkit renders in the right-side pane when an agent opens a case

## License

MIT
