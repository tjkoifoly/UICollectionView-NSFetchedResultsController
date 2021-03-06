# `UICollectionView+NSFetchedResultsController`

This is an example of how to use the new `UICollectionView` with `NSFetchedResultsController`. The trick is to queue the updates made through the `NSFetchedResultsControllerDelegate` until the controller *finishes* its updates. `UICollectionView` doesn't have the same `beginUpdates` and `endUpdates` that `UITableView` has to let it work easily with `NSFetchedResultsController`, so you have to queue them or you get internal consistency runtime exceptions.

# Setup

Clone the repo and look in the `UICollectionViewControllre` subclass. The logic inside the `.m` file shows how to queue updates.

Section updates are stored in `_sectionChanges` while udates to objects within sections are stored in `_objectChanges`. When `controllerDidChangeContent:` is called, these updates are dequeued. 

# Credit

Most of the logic for this is taken from [this gist](https://gist.github.com/4440c1cba83318e276bb).
