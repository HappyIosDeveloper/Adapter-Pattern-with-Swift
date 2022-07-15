# Adapter-Pattern-with-Swift
Here is a very basic &amp; simple practice to understand the adapter pattern.

## you can also download the provided playground file.

    import Foundation
    
    ///  Here is the Automative class with ability for Automitives
    class Automotive {
        func moveOnWheels() {
            print("moving...")
        }
    }
    
    /// A car with automotive abiliies
    class Car: Automotive {
        var name: String?
        var numberOfSeets: Int?
        var numberOfDoors: Int?
        var color: CarColor?
        enum CarColor { case red, blue, white, black }
        init(name: String, color: CarColor) {
            self.name = name
            self.color = color
        }
    }
    
    /// A plane without the automative abilities but we want it to have some of it
    class Plane {
        var name: String?
        var numberOfEngines: Int?
        init(name: String) {
            self.name = name
        }
    }
    
    // MARK: car can roll on wheels
    let car = Car(name: "car", color: .red)
    car.moveOnWheels()
    
    // car can't roll on wheels
    let plane = Plane(name: "plane")
    // creating the adapter
    let palaneAdapter = PlaneAdapter(plane: plane)
    // now plane is also can roll on wheels
    palaneAdapter.moveOnWheels()
    
    /// Here is the plane adapter
    class PlaneAdapter: Automotive {
        var plane: Plane
        init(plane: Plane) {
            self.plane = plane
        }
        override func moveOnWheels() {
            print("now the \(plane.name ?? "?") is moving...")
        }
    }
    
