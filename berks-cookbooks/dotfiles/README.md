chef_dotfiles Cookbook
======================

Chef recipie for installing dotfiles for users.

Attributes
----------
<table>
  <tr>
    <th>Key</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><tt>["dotfiles"]["repo"]</tt></td>
    <td>String</td>
    <td>Repository for the dotfiles</td>
  </tr>
  <tr>
    <td><tt>["dotfiles"]["users"]</tt></td>
    <td>Array</tt>
    <td>Which users they should be installed for</td>
  </tr>
  <tr>
    <td><tt>["dotfiles"]["files"]</tt></td>
    <td>Array</td>
    <td>which files to install/symlink</td>
  </tr>
</table>

Usage
-----
Just include `dotfiles` in your node's `run_list`:

```json
{
  "name":"my_node",
  "run_list": [
    "recipe[dotfiles]"
  ]
}
```

For vagrant just add the recipe
```
chef.add_recipe "chef_dotfiles"
```

and configure the users attribute
```
dotfiles: {
  users: ["my", "users"]
}
```

License
-------

chef_dotfiles is licensed under the MIT License (http://www.opensource.org/licenses/MIT).
