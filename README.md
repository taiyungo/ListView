# ListView

[![CI Status](http://img.shields.io/travis/matanwrites/ListView.svg?style=flat)](https://travis-ci.org/matanwrites/ListView)
[![Version](https://img.shields.io/cocoapods/v/MTListView.svg?style=flat)](http://cocoapods.org/pods/MTListView)
[![License](https://img.shields.io/cocoapods/l/MTListView.svg?style=flat)](http://cocoapods.org/pods/MTListView)
[![Platform](https://img.shields.io/cocoapods/p/MTListView.svg?style=flat)](http://cocoapods.org/pods/MTListView)


A ListView with a simple API to stack different kind of cells vertically

## Example

```swift
class ViewController: UIViewController {

    @IBOutlet weak var collectionView: UICollectionView! {
        didSet { collectionView.dataSource = datasource }
    }
    
    let datasource = ListDatasource()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        datasource.register(
            cell: LabelCell.self,
            at: 0,
            setupClosure: { ($0 as! LabelCell).setup(with: "bla") }
        )

        datasource.register(
            cell: ButtonCell.self,
            at: 1,
            setupClosure: { ($0 as! ButtonCell).setup(with: "bla") }
        )
        
        datasource.register(nib: NibCell.nib, for: collectionView, cell: NibCell.self, at: 2) {
            ($0 as! NibCell).setup(with: "bla")
        }
    }
}
````

To run the example project, clone the repo, and run `pod install` from the Example directory first.


## Installation

MTListView is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod 'MTListView'
```


## Author

matanwrites, https://twitter.com/matanwrites

## License

MTListView is available under the MIT license. See the LICENSE file for more info.

