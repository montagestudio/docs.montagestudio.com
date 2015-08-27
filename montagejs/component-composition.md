---

layout: docs
title: Component Composition

this-page: component-composition

---

组件构成
=======
你的应用是这样被构建出来的，在你的HTML模板文件中定义各种MontageJS的组件，然后把它们组合在一起。

## `Repetition`

它是一个重复`content`数组的组件。以下的定义会告诉`Repetition`组件重复`li`，也就是重复它对应的`Text`组件，重复的次数是`content`数组的长度（在这个列子中是三次）。

	<script type="text/montage-serialization">
	{
	    "repetition": {
	        "prototype": "montage/ui/repetition.reel",
	        "properties": {
	            "element": {"#": "repetition"},
	            "content": [1,2,3]
	        }
	    }
	    "text": {
	        "prototype": "montage/ui/text.reel",
	        "properties": {
	            "element": {"#": "text"},
	            "value": "hello"
	        }
	    }
	}
	</script>

	<body>
	    <ul data-montage-id="repetition">
	        <li data-montage-id="text"></li>
	    </ul>
	</body>
	

## `Condition`
例如以下的`Condition`组件设置只有当`condition`属性的值为`true`的时候才显示`span`的`value` "This is the truth"。在这个例子中`condition`为`false`，使得`span`不显示。

	<script type="text/montage-serialization">
	{
	    "condition": {
	        "prototype": "montage/ui/condition.reel",
	        "properties": {
	            "element": {"#": "condition"},
	            "condition": false
	        }
	    }
	    "text": {
	        "prototype": "montage/ui/text.reel",
	        "properties": {
	            "element": {"#": "text"},
	            "value": "This is the truth"
	        }
	    }
	}
	</script>

	<body>
	    <div data-montage-id="condition">
	        <span data-montage-id="text"></span>
	    </div>
	</body>
	

## `Substitution`
`Substitution`组件是让一组组件根据`value`的值只显示一个。

	<script type="text/montage-serialization">
	{
	    "customerNameSubstitution": {
	        "prototype": "montage/ui/substitution.reel"
	        "properties": {
	            "element": {"#": "customerNameSubstitution"},
	            "switchComponents": {
	                "read" : "montage/ui/text.reel"
	                "edit" : "montage/ui/input-text.reel"
	            }
	            "switchValue": "read"
	        },
	        "bindings": {
	            "value": {
	                "<-": "@customer.name"
	            }
	        }
	    }
	}
	</script>

	<body>
	    Customer name: <div data-montage-id="customerNameSubstitution"></div>
	</body>
	

## 组件模板参数
`CustomComponent`组件可以使用一个模板参数来替换它里面的内容。模板参数是指具有 `data-arg`属性的DOM节点。这个节点被标识成一个占位符，它的具体内容由外部的使用者提供。

	<script type="text/montage-serialization">{
	    "CustomComponent": {
	        "prototype": "my/custom-component.reel",
	        "properties": {
	            "element": {"#": "CustomComponent"}
	        }
	    }
	    "text": {
	        "prototype": "montage/ui/text.reel",
	        "properties": {
	            "element": {"#": "text"},
	            "value": "I'm included."
	        }
	    }
	}</script>

	<body>
	    <div data-montage-id="CustomComponent">
	        <!-- inner template -->
	        <span data-montage-id="text"></span>
	    </div>
	</body>
	
`CustomComponent` 的模板: `my/custom-component.reel/custom-component.html`


	<script type="text/montage-serialization">{
	    "owner": {
	        "prototype": "my/custom-component.reel"
	    }
	}</script>

	<body>
	    <div>
	        <!-- template argument to be replaced by inner template -->
	        <span data-arg="*"></span>
	    </div>
	</body>
