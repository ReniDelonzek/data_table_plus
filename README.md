Table based on DataTable stock and [DataTable2](https://pub.dev/packages/data_table_2), with some improvements

This is a simple table implementation, where the goal is to add small improvements to the default table avoiding interface breaks.

For a more advanced view, with support for pagination, sorting, search and more, see [select_any](https://pub.dev/packages/select_any)

## Differences
- Table expands horizontally according to content size (https://github.com/maxim-saplin/data_table_2/issues/8])
- Support Custom Rows
- Support specify width columns 
- Possibility to hide select all button
- Possibility to hide selection button and continue capturing line click events

## Usage

1. Add reference to pubspec.yaml.


2. Code:
```dart
import 'package:data_table_plus/data_table_plus.dart';
import 'package:flutter/material.dart';
import 'package:flutter/rendering.dart';

class DataTablePlusDemo extends StatefulWidget {
  const DataTablePlusDemo();

  @override
  _DataTablePlusDemoState createState() => _DataTablePlusDemoState();
}

class _DataTablePlusDemoState extends State<DataTablePlusDemo> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
        padding: const EdgeInsets.all(16),
        child: SingleChildScrollView(
          scrollDirection: Axis.horizontal,
          child: SingleChildScrollView(
            child: DataTablePlus(
              columns: [
                DataColumnPlus(
                  label: Text('Column A'),
                ),
                DataColumn(
                  label: Text('Column B'),
                ),
                DataColumn(
                  label: Text('Column C'),
                ),
                DataColumn(
                  label: Text('Column D'),
                ),
                DataColumn(
                  label: Text('Column NUMBERS'),
                  numeric: true,
                ),
              ],
              rows: List<DataRow>.generate(
                  100,
                  (index) => DataRow(cells: [
                        DataCell(Text('A' * (10 - index % 10))),
                        DataCell(Text('B' * (10 - (index + 5) % 10))),
                        DataCell(Text('C' * (15 - (index + 5) % 10))),
                        DataCell(Text('D' * (15 - (index + 10) % 10))),
                        DataCell(Text(((index + 0.1) * 25.4).toString()))
                      ])),

              /// Custom
              showCheckboxSelectAll: false,
              customRows: [
                /// Add column above header
                CustomRow(
                    index: -1,
                    cells: [
                      Text('My custom Column'),
                      TextButton(onPressed: () {}, child: Text('Button')),
                      Container(),
                      Container(),
                      Container(),
                    ],
                    typeCustomRow: TypeCustomRow.ADD),

                /// Add column below header
                CustomRow(
                    index: 2,
                    cells: [
                      Text('My custom Column'),
                      TextButton(onPressed: () {}, child: Text('Button')),
                      Container(),
                      Container(),
                      Container(),
                    ],
                    typeCustomRow: TypeCustomRow.ADD)
              ],
            ),
          ),
        ),
      ),
    );
  }
}
```

## TODO List
[ ] - Add more examples<br>
[ ] - Add Tests
