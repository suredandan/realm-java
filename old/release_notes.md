!!!!!!!!!!!!!!!NOTE - NOTE!!!!!!!!!!!!!!!!!!!!!
Remember to increase the TIGHTDB_JNI_VERSION in com_tightdb_internal_Util.cpp and com.tightdb.internal.Util.java
      when the JNI interface is changed.
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Template
=============================================================
x.x.x Release notes (yyyy—MM-dd)

Java
----
The Java API has been updated and your code will break!

### Bugfixes:

* None.

### API breaking changes:

* `???`

### Enhancements:

* `???`

-------------

### Internals:

* `???`

=============================================================
0.6.0 Release notes (yyyy—MM-dd)

Java
----

### Bugfixes:

* None.

### API breaking changes:

* None.

### Enhancements:

* `maximumDate` has been added to `Table`, `TableView` and `Query`
* `minimumDate` has been added to `Table`, `TableView` and `Query`

-------------

### Internals:

* `???`

=============================================================
0.5.0 Release notes (2014-04-02)

Java
----
Release due to update of C++ (core) library.

### Bugfixes:

* None.

### API breaking changes:

* None.

### Enhancements:

* None.

-------------

### Internals:

* Remove obsolete function `Java_com_tightdb_internal_Util_nativeGetVersion()`




25-March-2014:
=================
+ Group, SharedGroup, Table, TableView & Query now implements Closeable

06-February-2014:
=================
+ Added get-version and set-version to build.sh.

04-February-2014:
=================
+ Query.subtable() and Query.endSubtable() is now implemented.
! API Breaking change: The following methods in both Table and TableView class
  has been renamed to be consistent with other methods:
  - sumInt()     -> sumLong().
  - maximumInt() -> maximumLong().
  - minimumInt() -> minimumLong().
  - averageInt() -> averageLong().
 + Accessing a TableView after it's parent table has been changed, is now detected,
   and an exception is thrown.
 + Version API introduced. Not to be documented yet.

18-December-2013:
=================
! Bugfix: Table and TableView's findFirst*() methods now correctly returns -1
on 32 bit architectures when the value can't be found.

12-December-2013:
================
! BREAKING CHANGE: SubTableSchema renamed to SubtableSchema.
! BREAKING CHANGE: All methods with *subTable* renamed to *subtable*.

25-November-2013:
================
+ Query objects are now validated when executed to avoid breaking core.

19-November-2013:
================
+ Added sort() to views in typed interface on bool, date and int columns.
+ Check for returning -1 on 32-bit machines, when e.g. column name not found.

14-November-2013:
================
+ SQLite examples now runs on JDK 7.

11-November-2013:
================
+ table.getSortedView now uses native method - making it faster.

07-November-2013:
================
+ Avoiding more namespace issues when defining typed tables.
+ Added com.tightdb.IllegalMixedTypeException as a runtime exception. Is thrown when getting a wrong type from a Mixed object.

06-November-2013:
================
+ Added getSourceRowIndex() method on TableView.

25-October-2013:
================
+ Added lookup(String val) method to typed table.

25-October-2013:
================
+ Added addEmptyRow() method to typed table.
+ Added findFrom() method to typed query.

15-October-2013:
================
+ Table.get*() with negative column index no longer breaks core, but throws exception instead.

13-October-2013:
================
+ dist-deb target in build.sh, updating debian/changelog.in.

09-October-2013:
===============
+ Added support for Async durability in SharedGroup.
+ Added ShareGroup.reserve(bytes)

08-October-2013:
================
+ Added where() on TableOrView interface.
+ Added where() in TableView.
+ Added queries on views in the typed interface.

30-September-2013:
==================
+ TableSchema interface added, declaring methods for adding, removing and renaming columns on tables and getting a SubTableSchema.
+ Table implements methods from TableSchema interface.
+ SubTableSchema class added, implementing methods from TableSchema interface, allowing dynamic schema changes on subtables.

27-September-2013:
==================
! BREAKING CHANGE: Removed named column cursors from rows in typed interface. Now only traditional getters/setters are allowed.
! BREAKING CHANGE: Because of the above subtables in Mixed columns are not supported, until a better implementation is made.
! BREAKING CHANGE: Removed shortnames for query methods. (eq, neq, lt, lte, gt, gte).
! BREAKING CHANGE: Renamed Qurey equal to equalTo, and notEqual to notEqualTo.
+ Added getDistinctView() method on Table.
+ added getSortedView() method on Table.

24-September-2013:
==================
+ Added com.tightdb.Table.equals() and fixed com.tightdb.Group.equals().

23-September-2013:
==================
+ Added com.tightdb.IOException, as a RuntimeException can be thrown from all methods operating on files, like Group(file), SharedGroup(file) etc.

20-September-2013:
==================
+ Added View.getColumnCount(), View.getColumnIndex(colIndex), View.getColumnName(colIndex), View.getColumnType(colIndex) to Dynamic interface.
- Removed Table.getColumnCount(), Table.getColumnIndex(colIndex), Table.getColumnName(colIndex), Table.getColumnType(colIndex) from Typed interface.
! BREAKING CHANGE: Added limit parameter to all query aggregates which already had a start, and stop parameter.


19-September-2013:
==================
+ Multiple tables of same type in typed interface can be added to same group, by specifying a custom name in the constructor.


16-September-2013:
=================
! BREAKING CHANGE: Removed ByteBuffer as type for Binary. Added byte[] as only type for Binary in both dynamic and typed interface.


10-September-2013:
==================
- Deprecated ReadTransaction.close()
+ WriteTransaction.commit() now throws IllegalStateException.

09-September-2013:
==================
+ Added Table.toString(), Table.toString(maxRows), Table.rowToString(row).
+ Added TableView.toString(), TableView.toString(maxRows), TableView.rowToString(row).
+ Added Group.toString(), toJson(), equals().
+ Added Mixed.getReadableValue().
+ Added SharedGroup.hasChanged().
+ Added validation of parameters in all methods. Exceptions are now thrown if invalid parameters are passed.

06-September-2013:
=================
! BUGFIX: Fixed small leak in TableQuery.

04-September-2013
===============
+ Added TableQuery.equal for Date.
+ Added TableQuery.eq for Date.
+ Added TableQuery.notEqual for Date.
+ Added TableQuery.neq for Date.
+ Added TableQuery.greaterThan for Date.
+ Added TableQuery.gt for Date.
+ Added TableQuery.greaterThanOrEqual for Date.
+ Added TableQuery.gte for Date.
+ Added TableQuery.lessThan for Date.
+ Added TableQuery.lt for Date.
+ Added TableQuery.lessThanOrEqual for Date.
+ Added TableQuery.lte for Date.
+ Added TableQuery.between for Date.

02-September-2013
===============
! BREAKING CHANGE: ColumnType constants have been renamed, e.g ColumnTypeString is now called STRING etc.
! BREAKING CHANGE: All insert() methods in Table class working on just 1 column have been hidden from the developer.

13-August-2013:
===============
+ Table.add() now returns row index of the added row.
! BREAKING CHANGE: Group() now takes a new OpenMode parameter and not a boolean.
  It now supports multiple ways to open a group. (ReadOnly, ReadWrite, WriteNoCreate).
+ Added Group.commit().
+ Added Group.equals().

04-August-2013:
===============
+ Experimental Table.findSortedLong() replaced by Table.lowerBoundLong() and Table.upperBoundLong() because these provide more flexibility, and it follows similar changes in the core library. (Kristian Spangsege).

05-July-2013:
============
+ Exception now thrown when calling a method on a closed Group().
! Proper exception is now thrown if group.writeToFile() is called on an existing file.

06-06-2013:
===========
+- at() in Table and TableView is now deprecated. Use get() instead.
+  added SharedGroup::close() method which will do a rollback() if needed.
   Meant to be used in a finally {} clause after a transaction.

16-05-2013:
===========
* Removing shell scripts for compiling examples (ant will also be installed).

07-05-2013:
===========
! BUGFIX: Removed memory leak, which occurred when creating a Group object.


03-05-2013:
===========
+ Added Table::count() methods and Table::lookup() (still missing documentation..)
+ Added QuickBenchmark example.

03-03-2013:
===========
+ Added Table::addColumn(), renameColumn(), removeColumn().

??
==
- Renamed Group::getTableCount() to size().
- Renamed TableBase to Table, TableViewBase to TableView.
+ Added support for Float and Double.

18-12-2012:
===========
+ Added TableBase: insert(), add(), set() which can insert/add/set all values for a row.
- Deprecated use of field based insert*() methods.

27-11-2012:
===========
+ Added ReadTransactions class and testcases for WriteTransactions.
+ Added TableViewBase:Average support.

15-11-2012:
===========
+  Changed multiple methods in QueryBase to not use TableBase as parameter.
+  Added TableBase where() method.

8-10-2012:
==========
+	Added 'TableQuery: tableview(TableViewBase tv)' for querying TableViews.
+	average() fixed to return correct double.
+	Added 'TableBase: distinct()' to return a distinct TableView.

6-9-2012:
=========
Table:
+	void removeLast()
+	ColumnType getMixedType(long columnIndex, long rowIndex);
+	void clearSubTable(long columnIndex, long rowIndex);
+	long getSubTableSize(long columnIndex, long rowIndex);
+	double average(long columnIndex);
+	String toJson();
LongRowSet:
+	public double average() 		!!! FIX in NAtive to return double!

TableView:
FIX implement nativeAverage()