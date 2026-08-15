# BarTender

## Introduction

BarTender is a software platform for designing and controlling the production of labels, barcodes, RFID tags, cards, and other printed items. Its architecture separates document design from the data and operational systems that supply variable content. A template can therefore contain fixed elements such as logos, captions, and layout geometry while receiving product identifiers, quantities, dates, serial numbers, or other values from external data sources at print time.

The software is organized around several functional components. BarTender Designer is used to create and modify document templates. Print Station provides a simplified interface for operators who need to select predefined documents and print them without changing their designs. Print Portal provides browser-based access to documents in environments where printing must be initiated from different client devices. Automation-oriented editions add integration, monitoring, administration, and centralized management capabilities.

A document is associated with a printer and its media configuration, so page dimensions, orientation, item spacing, and stock settings directly affect the rendered result. Changing the target printer can therefore require layout adjustments. BarTender also supports database connections, print-time data entry forms, serialization, and objects such as barcodes, pictures, formatted text, and RFID or other encoder objects.

For IT teams, BarTender is best treated as a printing subsystem rather than only a label editor. A production deployment can combine templates, databases, printers, licensing services, centralized logging, security controls, and automated workflows. This allows business applications to retain ownership of operational data while BarTender converts that data into controlled physical output.

## Template Design, Data Sources, and Print-Time Input

A BarTender document should be designed against the actual printer and media configuration that will be used in production. The design area represents the physical stock, including item dimensions, orientation, number of items per page, and spacing between items. These parameters are established through the New Document Wizard or Page Setup. If a document is moved to a printer with different supported media, BarTender can adjust the design area, but object positions may no longer fit correctly. For this reason, printer and stock configuration should be treated as part of the template deployment rather than as an incidental print setting.

Templates can contain barcode objects, text, pictures, lines, shapes, and encoder objects. Text objects can also use formatted content such as RTF, HTML, or XAML where the application requires richer formatting. Barcode and encoder objects can be bound to dynamic data rather than containing fixed values.

External data is configured through Database Setup. Depending on the source, BarTender can retrieve records from files or database systems and expose their fields through the Data Sources pane. A field can then be associated with a barcode, text object, or encoder object. During development, the Live Database Navigator or Print Preview can be used to verify how actual records appear in the template.

Not every value needs to come from a database. Data Entry Forms allow operators to provide values when a print job starts. For example, a warehouse operator can enter a package weight or production date while the product identifier and description continue to come from the database. This keeps variable operational input separate from the reusable template.

## Administration, Security, and Operational Monitoring

In automated environments, BarTender requires centralized administration of licensing, system data, security, files, and operational events. Automation editions use Seagull License Server to monitor printer licensing. BarTender can automatically discover the server, or administrators can specify its network address manually. When automatic discovery is unreliable because of routing or firewall configuration, the preferred server, port, timeout, and connection-attempt settings can be configured explicitly and tested from Licensing Setup.

The BarTender System Database provides centralized storage for operational information such as application events, print-job records, security checks, template information, and revision-related data. A default installation can use SQL Server Express, while larger or distributed environments can use a separate database server. A centralized database is particularly useful when several BarTender installations need to share historical information or when high print volumes generate substantial logging data.

Security can be applied at both application and document levels. Application-level controls can restrict configuration, document modification, or printing for particular users and groups. Document-level protection can restrict opening, editing, or script modification. Document encryption provides an additional control for sensitive templates; encrypted documents require the appropriate encryption configuration when moved between systems.

For controlled template development, Enterprise Automation environments can use Librarian to centralize files, enforce check-in and check-out, maintain revision history, and restore previous versions. Administrators can also define standardized locations for documents, images, and scripts and export these location settings for deployment to other installations.

Operational troubleshooting should use BarTender's logging facilities. Application messages can be written to the System Database or text files and filtered by severity or selected message types. E-mail alerts can notify administrators about defined warnings and errors. This provides an actionable monitoring path: detect an event, retain its context, identify the affected workstation or print operation, and investigate the corresponding template, data source, printer, or infrastructure component.
