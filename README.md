# UICollectionViewHorizontalPaging


Swift 5 / Xcode 12
Card Style UICollectionView with horizontal scroll and paging

![Alt Text](https://github.com/FatCucumber/UICollectionViewHorizontalPaging/blob/main/UICollectionViewHorizontalPaging/previewgif.gif)


UICollectionView Setting

![Setting1](https://i.imgur.com/REkg8LM.jpg)

![Setting2](https://i.imgur.com/MGGms0g.jpg)



ViewController.swift
```swift
import UIKit

class ViewController: UIViewController, UICollectionViewDelegate, UICollectionViewDataSource, UICollectionViewDelegateFlowLayout {
    
    //MARK: Connect CollectionView Outlet
    @IBOutlet weak var SampleCollectionView: UICollectionView!
    var CollectionData = ["Item 1","Item 2","Item 3","Item 4"]
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        //MARK: CollectionView dataSource & Delegate
        self.SampleCollectionView.dataSource = self
        self.SampleCollectionView.delegate = self
        
        //MARK: Register Cell Nib
        self.SampleCollectionView.register(UINib(nibName: "SampleCollectionViewCell", bundle: nil), forCellWithReuseIdentifier: "cell")
    }
    
    //MARK: Configure CollectionView
    func collectionView(_ collectionView: UICollectionView, numberOfItemsInSection section: Int) -> Int {
        return CollectionData.count
    }
    func collectionView(_ collectionView: UICollectionView, cellForItemAt indexPath: IndexPath) -> UICollectionViewCell {
        let cell = SampleCollectionView.dequeueReusableCell(withReuseIdentifier: "cell", for: indexPath) as! SampleCollectionViewCell
        cell.title.text = CollectionData[indexPath.row]
        return cell
    }
    func collectionView(_ collectionView: UICollectionView, layout collectionViewLayout: UICollectionViewLayout, sizeForItemAt indexPath: IndexPath) -> CGSize {
        return CGSize(width: SampleCollectionView.frame.width - 30, height: SampleCollectionView.frame.height - 15)
    }

}
```
