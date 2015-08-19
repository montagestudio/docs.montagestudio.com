---

layout: docs
title: MontageJS Substitution UI Container

prev-page: repetition
this-page: substitution
next-page: overlay

---

#Substitution

`Substitution`组件的作用是控制一组元素，每次显示其中的一个。每个元素有一个特殊属性。`Substitution`将这个属性的值设置给`switchValue`属性来决定显示哪一个元素。

在`Subsititution`中的元素通过DOM的`data-arg`属性进行唯一标识符配置。这个就是被`Subsititution`使用的特殊属性。

##模版API

###实例1

	"substitution": {
	    "prototype": "montage/ui/substitution.reel",
	    "properties": {
	        "element": {"#": "substitution"},
	        "switchValue": "profile"
	    }
	}

&nbsp;

	<div data-montage-id="substitution">
	    <div data-arg="profile">
	        First Name: Homer
	        Last Name: Simpson
	        Address: 742 Evergreen Terrace
	    </div>
	    <div data-arg="contact">
	        Telephone: 555-3223
	        Email: homer@simpson.web
	    </div>
	</div>
	
###实例2

Montage框架的其他组件同样可以作为`Substitution`的参数。

	"substitution": {
	    "prototype": "montage/ui/substitution.reel",
	    "properties": {
	        "element": {"#": "substitution"},
	        "switchValue": "profile"
	    }
	},

	"userProfile": {
	    "prototype": "ui/user-profile.reel",
	    "properties": {
	        "element": {"#": "userProfile"}
	    }
	},

	"userContact": {
	    "prototype": "ui/user-contact.reel",
	    "properties": {
	        "element": {"#": "userContact"}
	    }
	}
	
&nbsp;

	<div data-montage-id="substitution">
	    <div data-arg="profile" data-montage-id="userProfile"></div>
	    <div data-arg="contact" data-montage-id="userContact"></div>
	</div>
	
##程序API

* `addSwitchElement(key, element)` - 添加一个元素作加入显示/隐藏列表。元素自己必须是根元素。
* 'switchValue' - 设置需要显示的元素。
