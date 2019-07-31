### Manually

---

1\. Download and drop [HorizontalPageControlView.swift in your project

2\. Configuration

Usage example
-------------

---

1\. Drop HorizontalPageControlView.swift in your project

2\. Make UIView in StoryBoard

3\. Designate Custom Class ‘HorizontalPageControlView’ in your PageControlView

4\. Add code

```swift
@IBOutlet weak var pageControl      : HorizontalPageControlView!

override func viewDidLoad() {
    super.viewDidLoad()
    self.setPageControlTotalCount()
}

func setPageControlTotalCount() {
  // must set HorizontalPageControlView totalPageCount
  self.pageControl.totalPageCount = 7
}

extension ViewController: UICollectionViewDelegate {
    func scrollViewDidScroll(_ scrollView: UIScrollView) {
        
        // must set HorizontalPageControlView indicatorOffset
        let offset = scrollView.contentOffset.x / scrollView.bounds.width
        self.pageControl?.indicatorOffset = offset
    }
}
```

### Attribute

---

```swift
// set SelectedColor in indicator
@IBInspectable var selectedColor: UIColor? {
    didSet {
        self.setNeedsDisplay()
    }
}
// set TotalCount
var totalPageCount  : Int = 0 {
    didSet {
        self.setNeedsDisplay()
    }
}
// set Offset
var indicatorOffset : CGFloat = 0 {
    didSet {
        self.setNeedsDisplay()
    }
}
// usally get index in indicator
var selectedPosition: Int {
    get { return Int(round(self.indicatorOffset)) }
    set { self.indicatorOffset = CGFloat(newValue) }
}
```