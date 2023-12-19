# SwiftUI-Search-Demo
SwiftUI Search Demo of List and Grid.
# The first part
![IMG_1274](https://github.com/S-way520/SwiftUI-Search-Demo/assets/95877651/d8558cd0-1a63-4c28-a531-69d74b2d16f3)
# The second part
Code file 1
```swift
import SwiftUI
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```
Code file 2
```swift
/*
// (1) MARK: List Search Demo
import SwiftUI
struct ContentView: View {
    @State private var searchText = ""
    let items = ["ABC 1", "ADE 2", "AFG 3", "AHI 4", "AJK 5"]
    var body: some View {
        NavigationView {
            VStack {
                TextField("Search", text: $searchText)
                    .padding()
                    .textFieldStyle(RoundedBorderTextFieldStyle())
                List {
                    ForEach(items.filter { searchText.isEmpty || $0.localizedCaseInsensitiveContains(searchText) }, id: \.self) { item in
                        HStack {
                            Text(item)
                        }
                    }
                }
                .listStyle(PlainListStyle())
            }
            .navigationTitle("List Search Demo")
        }
    }
}
*/
// (2) MARK: Grid Search Demo
import SwiftUI
struct ContentView: View {
    @State private var searchText = ""
    let items = ["ABC 1", "ADE 2", "AFG 3", "AHI 4", "AJK 5"]
    var body: some View {
        NavigationStack {
            VStack {
                TextField("Search", text: $searchText)
                    .padding()
                    .textFieldStyle(RoundedBorderTextFieldStyle())
                ScrollView {
                    LazyVGrid(columns: [GridItem(.flexible()), GridItem(.flexible())], spacing: 16) {
                        ForEach(items.filter { searchText.isEmpty || $0.localizedCaseInsensitiveContains(searchText) }, id: \.self) { item in
                            Text(item)
                                .frame(minWidth: 0, maxWidth: .infinity, minHeight: 100)
                                .background(Color.blue)
                                .foregroundColor(.white)
                                .cornerRadius(10)
                                .padding()
                        }
                    }
                    .padding()
                }
            }
            .navigationTitle("Grid Search Demo")
        }
    }
}
```
