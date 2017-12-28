# HypeSwift4WKWebview
Viewcontroller Swift 4.0 code for XCode 9.0 that will display a local HTML file

// Paste code below into XCODE viewController.swift


//
//  ViewController.swift
//  honk
//
//  Created by Nick Gressle on 9/23/17.
//  Copyright © 2017 nick gressle illustrations llc. All rights reserved.
//

import UIKit
import WebKit
class ViewController: UIViewController, WKNavigationDelegate {
    override func viewDidLoad() {
        super.viewDidLoad()
        let webView = WKWebView()
        let htmlPath = Bundle.main.path(forResource: "Honk", ofType: "html")
        let folderPath = Bundle.main.bundlePath
        let baseUrl = URL(fileURLWithPath: folderPath, isDirectory: true)
        do {
            let htmlString = try NSString(contentsOfFile: htmlPath!, encoding: String.Encoding.utf8.rawValue)
            webView.loadHTMLString(htmlString as String, baseURL: baseUrl)
        } catch {
            // catch error
        }
        webView.navigationDelegate = self
        view = webView
    }
}
