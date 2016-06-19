# EasyDropDownMenu
类似美团，糯米，大众点评的筛选排序菜单

## Join Us 
为了更好的完善此框架，希望更多对此框架有兴趣的朋友一起加入进来打造最好用最全面扩展最好的swift框架。
EasySwift官方QQ群：<mark>**542916901**</mark>

## Features
* 最简单，最快速的操作方式

## System Requirements
iOS 8.0 or above

## Installation
### As a CocoaPods Dependency
Add the following to your Podfile:

	pod 'EasyDropDownMenu'
	

### ScreenShot
![image](https://github.com/stubbornnessness/EasyDropDownMenu/blob/master/EasyDropDownMenuTest/EasyDropDownMenuTest/test.gif)

## Version
**V0.0.1** ---- 2016-6-19

* 首次发版
	
## Example
	import UIKit
	import EasyDropDownMenu

	class ViewController: UIViewController, YXJDropDownMenuDelegate, YXJDropDownMenuDataSource {

    lazy var classifys = ["美食", "今日新单", "电影", "酒店"]
    lazy var cates = ["自助餐", "快餐", "火锅", "日韩料理", "西餐", "烧烤小吃"]
    lazy var movices = ["内地剧", "港台剧", "英美剧"]
    lazy var hostels = ["经济酒店", "商务酒店", "连锁酒店", "度假酒店", "公寓酒店"]
    lazy var areas = ["全城", "芙蓉区", "雨花区", "天心区", "开福区", "岳麓区"]
    lazy var sorts = ["默认排序", "离我最近", "好评优先", "人气优先", "最新发布"]

    lazy var menu = YXJDropDownMenu.init(origin: CGPointMake(0, 64), andHeight: 44)

    override func viewDidLoad() {
        super.viewDidLoad()

        // self.navigationItem.rightBarButtonItem = UIBarButtonItem.init(title:"重新加载", style:UIBarButtonItemStyle.Plain, target:self, action:"menuReloadData")

        // 添加下拉菜单
        self.menu.delegate = self
        self.menu.dataSource = self

        self.menu.textColor = UIColor.blackColor()
        self.menu.textSelectedColor = UIColor.init(red: 69.0 / 255.0, green: 198 / 255.0, blue: 190 / 255.0, alpha: 1)
        self.view.addSubview(menu)

        // 创建menu 第一次显示 不会调用点击代理，可以用这个手动调用
        menu.selectDefalutIndexPath()
    }

    // MARK:右键点击事件
    func menuReloadData() {
        self.classifys = ["美食", "今日新单", "电影"]
        self.menu.reloadData()
    }
    // MARK:按钮事件
    func selectIndexPathAction(sender: AnyObject) {
        self.menu.selectIndexPath(YXJIndexPath(col: 0, row: 2, item: 2))
    }

    // MARK:YXJDropDownMenuDelegate
    func numberOfColumnsInMenu(menu: YXJDropDownMenu!) -> Int {
        return 3
    }
    func menu(menu: YXJDropDownMenu!, numberOfRowsInColumn column: Int) -> Int {
        if (column == 0) {
            return self.classifys.count
        } else if (column == 1) {
            return self.areas.count
        } else {
            return self.sorts.count
        }
    }
    func menu(menu: YXJDropDownMenu!, titleForRowAtIndexPath indexPath: YXJIndexPath!) -> String! {
        if (indexPath.column == 0) {
            return self.classifys[indexPath.row]
        } else if (indexPath.column == 1) {
            return self.areas[indexPath.row]
        } else {
            return self.sorts[indexPath.row]
        }
    }

    // MARK: new datasource
    func menu(menu: YXJDropDownMenu!, imageNameForRowAtIndexPath indexPath: YXJIndexPath!) -> UIImage! {
        if (indexPath.column == 0 || indexPath.column == 1) {
            return UIImage(named: "TestImgs.bundle/ic_filter_category_\(indexPath.row)")
        }
        return nil
    }
    func menu(menu: YXJDropDownMenu!, imageNameForItemsInRowAtIndexPath indexPath: YXJIndexPath!) -> UIImage! {
        if (indexPath.column == 0 || indexPath.column == 1) {
            return UIImage(named: "TestImgs.bundle/ic_filter_category_\(indexPath.item)")
        }
        return nil
    }

    // MARK: new datasource
    func menu(menu: YXJDropDownMenu!, detailTextForRowAtIndexPath indexPath: YXJIndexPath!) -> String! {
        if (indexPath.column < 2) {
            return "11"
        }
        return nil
    }
    func menu(menu: YXJDropDownMenu!, detailTextForItemsInRowAtIndexPath indexPath: YXJIndexPath!) -> String! {
        return "22"
    }
    func menu(menu: YXJDropDownMenu!, numberOfItemsInRow row: Int, column: Int) -> Int {
        if (column == 0) {
            if (row == 0) {
                return self.cates.count
            } else if (row == 2) {
                return self.movices.count
            } else if (row == 3) {
                return self.hostels.count
            }
        }
        return 0
    }
    func menu(menu: YXJDropDownMenu!, titleForItemsInRowAtIndexPath indexPath: YXJIndexPath!) -> String! {
        if (indexPath.column == 0) {
            if (indexPath.row == 0) {
                return self.cates[indexPath.item]
            } else if (indexPath.row == 2) {
                return self.movices[indexPath.item]
            } else if (indexPath.row == 3) {
                return self.hostels[indexPath.item]
            }
        }
        return nil
    }
    func menu(menu: YXJDropDownMenu!, didSelectRowAtIndexPath indexPath: YXJIndexPath!) {
        if (indexPath.item >= 0) {
            print("点击了 \(indexPath.column) - \(indexPath.row) - indexPath.item 项目")
        } else {
            print("点击了 \(indexPath.column) - \(indexPath.row) 项目")
        }
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
    }

	}
    
## 极致框架
* EasySwift是从2014年开始打造的贯穿整个Swift开发的整套解决方案，只为最简单，最高效，最全面，高扩展性，囊括最前沿的架构，思想在其中[EasySwift](https://github.com/stubbornnessness/EasySwift)

## License
EasyEmoji is licensed under the Apache License, Version 2.0 License. For more information, please see the LICENSE file.

