!NOTE: the first 2 letters follow the stable version of FLutter SDK upon which the package is based on (i.e. which sources are copied and modified) - if there're new APIs introuduced to DataTable and PaginatedDataTable with newer SDK relases those changes might not be present in the provided by this package widgets until the major and minor versions codes of this package match. The 3rd letter is the version of the package itself (most likely this part to be changed when bug fixes are).  

## 2.0.1

Fixed horizonalMargin (it was not accounted for when calculating column sizes, first and last columns where shrinked by this value)

## 2.0.0

Perf. optimization of DataTable.build(), finishing off the package for roll-out to pub.dev

## 2.0.0-dev.1

The very first relase to pub.dev