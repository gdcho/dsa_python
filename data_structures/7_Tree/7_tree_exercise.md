#### Data structures exercise: General Tree

1. Below is the management hierarchy of a company.

    ![ss](management_both.PNG)

Extent [tree class](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/7_Tree/7_tree.py) built in our
main tutorial so that it takes **name** and **designation** in data part of TreeNode class.
Now extend print_tree function such that it can print either name tree, designation tree or name and designation tree. As shown below,

   ![](all_trees.png)

Here is how your main function should will look like,
```
if __name__ == '__main__':
    root_node = build_management_tree()
    root_node.print_tree("name") # prints only name hierarchy
    root_node.print_tree("designation") # prints only designation hierarchy
    root_node.print_tree("both") # prints both (name and designation) hierarchy
```

Solution:
```py
class TreeNode:
    def __init__(self, name, role):
        self.name = name
        self.role = role
        self.children = []
        self.parent = None

    def get_level(self):
        level = 0
        p = self.parent
        while p:
            level += 1
            p = p.parent

        return level

    def print_tree(self, property_name):
        if property_name == "both":
            value = self.name + " (" + self.role + ")"
        elif property_name == 'name':
            value = self.name
        else:
            value = self.role

        spaces = ' ' * self.get_level() * 3
        prefix = spaces + "|__" if self.parent else ""
        print(prefix + value)
        if self.children:
            for child in self.children:
                child.print_tree(property_name)

    def add_child(self, child):
        child.parent = self
        self.children.append(child)

def build_management_tree():
    root = TreeNode("Nilupul", "CEO")

    cto = TreeNode("Chinmay", "CTO")
    infrastructure = TreeNode("Vishwa", "Infrastructure Head")
    cto.add_child(infrastructure)
    cto.add_child(TreeNode("Aamir", "Application Head"))

    infrastructure.add_child(TreeNode("Dhaval", "Cloud Manager"))
    infrastructure.add_child(TreeNode("Abhijit", "App Manager"))

    hr = TreeNode("Gels", "HR Head")
    hr.add_child(TreeNode("Peter", "Recruitment Manager"))
    hr.add_child(TreeNode("Waqas", "Policy Manager"))

    root.add_child(cto)
    root.add_child(hr)

    return root

if __name__ == '__main__':
    root_node = build_management_tree()
    print("Printing names only")
    root_node.print_tree("name") # prints only name hierarchy
    print("\nPrinting roles only")
    root_node.print_tree("role") # prints only role hierarchy
    print("\nPrinting both names and roles")
    root_node.print_tree("both") # prints both (name and role) hierarchy

```

[Solution](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/7_Tree/Exercise/management_hierarchy.py)

2. Build below location tree using **TreeNode** class

    ![](location_trees.png)

Now modify print_tree method to take tree level as input. And that should print tree only upto that level as shown below,

   ![](location_trees_all.png)

Solution:
```py
class TreeNode:
    def __init__(self, name):
        self.name = name
        self.children = []
        self.parent = None

    def get_level(self):
        level = 0
        p = self.parent
        while p:
            level += 1
            p = p.parent

        return level

    def print_tree(self, level):
        if self.get_level() > level:
            return
        spaces = ' ' * self.get_level() * 3
        prefix = spaces + "|__" if self.parent else ""
        print(prefix + self.name)
        if self.children:
            for child in self.children:
                child.print_tree(level)

    def add_child(self, child):
        child.parent = self
        self.children.append(child)

def build_location_tree():
    root = TreeNode("Global")

    india = TreeNode("India")
    gujarat = TreeNode("Gujarat")
    india.add_child(gujarat)
    karnataka = TreeNode("Karnataka")
    india.add_child(karnataka)
    gujarat.add_child(TreeNode("Ahmedabad"))
    gujarat.add_child(TreeNode("Baroda"))
    karnataka.add_child(TreeNode("Bangluru"))
    karnataka.add_child(TreeNode("Mysore"))

    usa = TreeNode("USA")
    newjersery = TreeNode("New Jersey")
    usa.add_child(newjersery)
    california = TreeNode("California")
    usa.add_child(california)
    newjersery.add_child(TreeNode("Princeton"))
    newjersery.add_child(TreeNode("Trenton"))
    california.add_child(TreeNode("San Francisco"))
    california.add_child(TreeNode("Mountain View"))
    california.add_child(TreeNode("Palo Alto"))

    root.add_child(india)
    root.add_child(usa)

    return root

if __name__ == '__main__':
    root_node = build_location_tree()
    print("Printing tree level 1")
    root_node.print_tree(1)
    print("Printing tree level 2")
    root_node.print_tree(2)
    print("Printing tree level 3")
    root_node.print_tree(3)

```

[Solution](https://github.com/codebasics/data-structures-algorithms-python/blob/master/data_structures/7_Tree/Exercise/location_hierarchy.py)


