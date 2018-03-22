# GifLoader
Simple UIImage Extension for load a Gif on a viewcontroller

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)


## Features

- [x] Load any Gif file and run on a loop.
- [x] Easy addon to your project.
- [x] Customizable animation duration.

## Installation

Simply copy and paste GifLoader File on your Project :)

## Usage

#### Step 01

Add UIView and UIImage view on you project file.

```
    class LandingViewController: UIViewController {
    
      @IBOutlet weak var loadingView: UIView!
      var loadingGifImageView: UIImageView!
    
      ///// ViewController Code ///
    
      .............
    
    }

```

#### Step 02

Add this extension file on your project ViewController.


```

     extension LandingViewController {
    
        ////// Loading View /////
    
        func hidesLoadingView() {
            self.view.sendSubview(toBack: self.loadingView)
            self.loadingView.alpha = 0.0
            if loadingGifImageView != nil {
                self.loadingGifImageView.removeFromSuperview()
                self.loadingGifImageView = nil
            }
        }
    
        func showLoadingView() {
            self.view.bringSubview(toFront: self.loadingView)
            self.loadingView.alpha = 0.6 // Adjust Background View alpha
        
            if self.loadingGifImageView == nil {
                let loadingGif = UIImage.gifImageWithName(name: "loading") //Your Gif image name
                self.loadingGifImageView = UIImageView(image: loadingGif)
                self.loadingGifImageView.frame = CGRect(x: 0, y: 0, width: 160.0, height: 24.0) // Adjust your Gif Image Size here.
                self.loadingGifImageView.center.x = self.loadingView.center.x // Adjust your Gif Image X position here.
                self.loadingGifImageView.center.y = self.loadingView.center.y // Adjust your Gif Image Y position here.
                self.loadingView.addSubview(self.loadingGifImageView)
            }
        }
    }

```

#### Step 03

Now You can simply use showLoadingView() to show Gif image and hidesLoadingView() to hide Gif image.

