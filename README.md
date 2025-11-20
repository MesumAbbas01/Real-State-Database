# Real Estate Management System - ERD Documentation

## 1. Introduction
This project presents an **Entity-Relationship Diagram (ERD)** for a Real Estate Management System.  
The diagram illustrates how all main components of the system are connected, including **clients, owners, properties, real estate companies, and transactions**.  

**Notation Used:** Chen notation  
- Rectangles = Entities  
- Diamonds = Relationships  
- Keywords describe connections  

This ERD provides a clear structure for managing the system and serves as a foundation for implementing the database.

---

## 2. Entities
There are **16 main entities**:

| Entity | Description |
|--------|-------------|
| Client | Person looking to buy or rent a property |
| Owner | Person who owns a property and wants to list it |
| Real_Estate_Company | Agencies managing properties and clients |
| Staff / Employee | Employees handling daily operations |
| Location | Area or city of the property |
| Property | The real estate item for sale or rent |
| Property_Type | Type of property (House, Apartment, Commercial) |
| Contract / Agreement | Junction table connecting clients, owners, companies, and properties |
| Payment | Records of payments made for a contract |
| Feedback / Review | Reviews given by clients |
| Maintenance_Request | Requests for property maintenance |
| Land_Records_Department | Maintains official property records |
| Sub_Registrar_Office | Handles legal registration of properties/contracts |
| Municipal_Authority | Approves zoning, development, property taxes |
| Stamp_Duty_Department | Manages taxes and stamp duty for contracts |
| Bank / Finance_Office | Provides loans to clients or owners |

> All entities are **strong entities**, capable of existing independently.

---

## 3. Relationships
Relationships connect the entities as follows:

| Entities | Keyword | Type | Notes |
|----------|---------|------|-------|
| Client – Real_Estate_Company | deals with | M:N | Handled via Contract / Agreement |
| Owner – Real_Estate_Company | lists with | M:N | Handled via Contract / Agreement |
| Real_Estate_Company – Staff | employs | 1:M | One company employs many staff |
| Property – Owner | belongs to | M:1 | Each property has one owner |
| Property – Location | located at | M:1 | Each property is in a location |
| Property – Property_Type | is of type | M:1 | Each property has one type |
| Property – Real_Estate_Company | managed by | M:1 | Each property is managed by one company |
| Client – Property | buys/rents | M:N | Multiple clients and properties, via Contract |
| Contract / Agreement – Client/Owner/Company/Property | connects | M:1 | Each contract links client, owner, company, property |
| Payment – Contract/Client/Owner | made for | M:1 | Payments linked to contracts |
| Feedback / Review – Client/Owner/Company/Property | about | M:1 | Client feedback on properties, owners, companies |
| Maintenance_Request – Property/Staff/Client | requested for | M:1 | Assigned to staff |
| Bank / Finance_Office – Client/Owner | provides loan to | M:1 | Banks provide loans |
| Land_Records_Department – Property | records | 1:M | Maintains property records |
| Sub_Registrar_Office – Contract/Property | registers | 1:M | Handles legal registration |
| Municipal_Authority – Property/Location | approves | 1:M | Approves zoning, development, taxes |
| Stamp_Duty_Department – Contract | applies | 1:M | Applies taxes/stamp duty |

**Optional / Extra Relationships:**

| Entities | Keyword | Notes |
|----------|---------|------|
| Staff – Maintenance_Request | handles | 1:M |
| Bank / Finance_Office – Property | finances | 1:M |
| Location – Municipal_Authority | under jurisdiction of | 1:M |

---

## 4. Design Decisions
- **M:N relationships** are handled with `Contract / Agreement` as a **junction table**, avoiding direct foreign keys in Client, Owner, or Company.
- No weak entities exist; all entities can exist independently.
- `Property_Type` is a regular entity.
- Followed **Chen notation**: rectangles for entities, diamonds for relationships, keywords describe connections.

---

## 5. Conclusion
The ERD clearly represents the Real Estate Management System structure:

- Handles all major relationships correctly  
- Ownership and dependencies are clear  
- Easily expandable for future development  
- Ready for database implementation  

**Tip:** Draw in Canva or similar tools using rectangles for entities, diamonds for relationships, and keywords. Include attributes inside rectangles for full implementation.

---

**End of Documentation**
