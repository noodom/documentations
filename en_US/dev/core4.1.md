## Core v4.1 | Plugin developers

### Optional modifications

#### List of parent objects

In v4.1 the display of the selection of the parent object of a device has been revised and unified. The list is now ordered, and indented according to the parent.

To have the same logic in the plugins, plugin / desktop / plugin file.php :

`` ''php
<select id="sel_object" class="eqLogicAttr form-control" data-l1key="object_id">
  <option value="">{{Aucun}}</option>
  <?php
  $options = '';
  foreach ((jeeObject::buildTree (null, false)) as $ object) {
    $options .= '<option value="' . $object->getId() . '">' . str_repeat('&nbsp;&nbsp;', $object->getConfiguration('parentNumber')) . $object->getName() . '</option>';
  }
  echo $ options;
  ?>
</select>
`` ''

> This modification is Core v4 compatible.0 and v3.x
