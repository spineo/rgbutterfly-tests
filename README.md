# rgbutterfly-tests (Swift)
Unit and UI Testing in Swift with XCTest framework and Accessibility. Requirements include Xcode 7, OS X 10.11 El Capitan, and iOS 9 (or later versions). The test frameworks bridge into the 'RGButterfly' App (Objective-C)

Dependencies: XCTest/XCTest.h (The XCTest file need to be added as a compile target to Tests under 'BuildPhases' for this to build)

Requirements for InitViewControllerTests:
* There is Network Connectivity
* The Jenkins server is running during the test

## General Structure
* Bridging header (RGButterflyTests-Bridging-Header.h): Interfaces with the Objective-C RGButterfly application
* Base Class (RGButterflyBaseTests.swift): Contains methods/assertions common to more than one controller test class.
* Model (DataModelTests.swift): Datamodel unit tests (uses CoreData/ManagedObject)
* Controllers: View Controllers unit tests (subclasses Base Class)

## Tests Common to All Controllers

#### Datamodel Counts
* Dictionary entities exist and have count greater than zero
* Dictionary entities count matches initialization file count
* Main entities exist and have count greater than zero (with exception of secondary keywords entities)
* Greater than zero PaintSwatches and TapAreas are associated with a MatchAssociation
* Number of TapAreas and PaintSwatches associated with a MatchAssociation are equal

#### Datamodel Relations
* MixAssociations have more than zero children
* All MixAssociationSwatches must be part of a MixAssociation
* MatchAssociations have more than zero children
* All TapAreas must be part of a MatchAssociation
* All PaintSwatches must be associated with a PaintSwatchType (with exception of 'MatchAssoc')
* All Keywords must be associated with a SwatchKeyword 

#### Controllers
* Controller can be instantiated with identifier

#### Views
* Main Controller View is not Nil
* Main Controller View title is not Nil

#### TableViews
* Any TableView associated with the Controller is not Nil
* Based on context, table view contains the correct number of sections

#### Connections
* All associated Segues are accessible
* Views controllers are embedded in Navigation Controllers where applicable
* Navigation Controllers have an associated identifier
* Actions associated with item/view selectors exist and can be performed
* Unwind Segues associated with item/view selectors exist and can be performed
* IBOutlets associated with item/view are not Nil
* Delegates associated with controller views

#### TitleView/NavBar/Toolbar Items
* SearchBars/Buttons associated with the TitleView are not Nil
* NavBar buttons exist and are associated with assigned tag value
* Toolbar items exist and are associated with assigned tag value
* Toolbar items are enabled/disabled based on context
* Flexible/Fixed Space items accounted for

## Controller-Specific Tests

### InitViewController
* Network Connectivity
* REST API Connectivity
* Activity Indicator label appears after 'viewDidAppear'
* Activity Indicator is animating after 'viewDidAppear'

### MainViewController
* Activity Indicator label appears after 'viewDidAppear'
* Activity Indicator is animating after 'viewDidAppear'
* Activity Indicator stops animating after 'viewDidDisappear'
* Subjective Color Names dictionary is loaded with greater than zero entities
* Keyword Index Titles array contains 26 elements (i.e., alphabet letters)
* PaintSwatches count is greater than zero
* CollectionViews associated with a tableView cell are not nil
* CollectionViews have more than zero items

_Performance Tests: Measure time to load each type of listing_

### PickerViewController
_None not covered above_

### ImageViewController
* ScrollView can be accessed with identifier and is not Nil
* ImageView can be accessed with identifier and is not Nil

### AssocTableViewController
_None not covered above_

### AddMixTableViewController
_None not covered above_

### MatchTableViewController
_None not covered above_

### SwatchTableViewController
_None not covered above_

### SettingsViewController
* tableView has the correct number of sections
* Each tableView section has more than zero rows

### AboutViewController
_None not covered above_

### DisclaimerViewController
_None not covered above_

## Nice to Have Tests
* Class delegates
* Layout Constraints
