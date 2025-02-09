:github_url: hide

.. DO NOT EDIT THIS FILE!!!
.. Generated automatically from Godot engine sources.
.. Generator: https://github.com/godotengine/godot/tree/master/doc/tools/make_rst.py.
.. XML source: https://github.com/godotengine/godot/tree/master/modules/multiplayer/doc_classes/MultiplayerSpawner.xml.

.. _class_MultiplayerSpawner:

MultiplayerSpawner
==================

**Inherits:** :ref:`Node<class_Node>` **<** :ref:`Object<class_Object>`

Automatically replicates spawnable nodes from the authority to other multiplayer peers.

Description
-----------

Spawnable scenes can be configured in the editor or through code (see :ref:`add_spawnable_scene<class_MultiplayerSpawner_method_add_spawnable_scene>`).

Also supports custom node spawns through :ref:`spawn<class_MultiplayerSpawner_method_spawn>`, calling :ref:`_spawn_custom<class_MultiplayerSpawner_method__spawn_custom>` on all peers.



Internally, ``MultiplayerSpawner`` uses :ref:`MultiplayerAPI.object_configuration_add<class_MultiplayerAPI_method_object_configuration_add>` to notify spawns passing the spawned node as the ``object`` and itself as the ``configuration``, and :ref:`MultiplayerAPI.object_configuration_remove<class_MultiplayerAPI_method_object_configuration_remove>` to notify despawns in a similar way.

Properties
----------

+---------------------------------+-------------------------------------------------------------------+------------------+
| :ref:`int<class_int>`           | :ref:`spawn_limit<class_MultiplayerSpawner_property_spawn_limit>` | ``0``            |
+---------------------------------+-------------------------------------------------------------------+------------------+
| :ref:`NodePath<class_NodePath>` | :ref:`spawn_path<class_MultiplayerSpawner_property_spawn_path>`   | ``NodePath("")`` |
+---------------------------------+-------------------------------------------------------------------+------------------+

Methods
-------

+-----------------------------+---------------------------------------------------------------------------------------------------------------------------------+
| :ref:`Node<class_Node>`     | :ref:`_spawn_custom<class_MultiplayerSpawner_method__spawn_custom>` **(** :ref:`Variant<class_Variant>` data **)** |virtual|    |
+-----------------------------+---------------------------------------------------------------------------------------------------------------------------------+
| void                        | :ref:`add_spawnable_scene<class_MultiplayerSpawner_method_add_spawnable_scene>` **(** :ref:`String<class_String>` path **)**    |
+-----------------------------+---------------------------------------------------------------------------------------------------------------------------------+
| void                        | :ref:`clear_spawnable_scenes<class_MultiplayerSpawner_method_clear_spawnable_scenes>` **(** **)**                               |
+-----------------------------+---------------------------------------------------------------------------------------------------------------------------------+
| :ref:`String<class_String>` | :ref:`get_spawnable_scene<class_MultiplayerSpawner_method_get_spawnable_scene>` **(** :ref:`int<class_int>` index **)** |const| |
+-----------------------------+---------------------------------------------------------------------------------------------------------------------------------+
| :ref:`int<class_int>`       | :ref:`get_spawnable_scene_count<class_MultiplayerSpawner_method_get_spawnable_scene_count>` **(** **)** |const|                 |
+-----------------------------+---------------------------------------------------------------------------------------------------------------------------------+
| :ref:`Node<class_Node>`     | :ref:`spawn<class_MultiplayerSpawner_method_spawn>` **(** :ref:`Variant<class_Variant>` data=null **)**                         |
+-----------------------------+---------------------------------------------------------------------------------------------------------------------------------+

Signals
-------

.. _class_MultiplayerSpawner_signal_despawned:

- **despawned** **(** :ref:`Node<class_Node>` node **)**

Emitted when a spawnable scene or custom spawn was despawned by the multiplayer authority. Only called on puppets.

----

.. _class_MultiplayerSpawner_signal_spawned:

- **spawned** **(** :ref:`Node<class_Node>` node **)**

Emitted when a spawnable scene or custom spawn was spawned by the multiplayer authority. Only called on puppets.

Property Descriptions
---------------------

.. _class_MultiplayerSpawner_property_spawn_limit:

- :ref:`int<class_int>` **spawn_limit**

+-----------+------------------------+
| *Default* | ``0``                  |
+-----------+------------------------+
| *Setter*  | set_spawn_limit(value) |
+-----------+------------------------+
| *Getter*  | get_spawn_limit()      |
+-----------+------------------------+

Maximum nodes that is allowed to be spawned by this spawner. Includes both spawnable scenes and custom spawns.



When set to ``0`` (the default), there is no limit.

----

.. _class_MultiplayerSpawner_property_spawn_path:

- :ref:`NodePath<class_NodePath>` **spawn_path**

+-----------+-----------------------+
| *Default* | ``NodePath("")``      |
+-----------+-----------------------+
| *Setter*  | set_spawn_path(value) |
+-----------+-----------------------+
| *Getter*  | get_spawn_path()      |
+-----------+-----------------------+

Path to the spawn root. Spawnable scenes that are added as direct children are replicated to other peers.

Method Descriptions
-------------------

.. _class_MultiplayerSpawner_method__spawn_custom:

- :ref:`Node<class_Node>` **_spawn_custom** **(** :ref:`Variant<class_Variant>` data **)** |virtual|

Method called on all peers when a custom spawn was requested by the authority using :ref:`spawn<class_MultiplayerSpawner_method_spawn>`. Should return a :ref:`Node<class_Node>` that is not in the scene tree.



\ **Note:** Spawned nodes should **not** be added to the scene with `add_child`. This is done automatically.

----

.. _class_MultiplayerSpawner_method_add_spawnable_scene:

- void **add_spawnable_scene** **(** :ref:`String<class_String>` path **)**

Adds a scene path to spawnable scenes, making it automatically replicated from the multiplayer authority to other peers when added as children of the node pointed by :ref:`spawn_path<class_MultiplayerSpawner_property_spawn_path>`.

----

.. _class_MultiplayerSpawner_method_clear_spawnable_scenes:

- void **clear_spawnable_scenes** **(** **)**

Clears all spawnable scenes. Does not despawn existing instances on remote peers.

----

.. _class_MultiplayerSpawner_method_get_spawnable_scene:

- :ref:`String<class_String>` **get_spawnable_scene** **(** :ref:`int<class_int>` index **)** |const|

Returns the spawnable scene path by index.

----

.. _class_MultiplayerSpawner_method_get_spawnable_scene_count:

- :ref:`int<class_int>` **get_spawnable_scene_count** **(** **)** |const|

Returns the count of spawnable scene paths.

----

.. _class_MultiplayerSpawner_method_spawn:

- :ref:`Node<class_Node>` **spawn** **(** :ref:`Variant<class_Variant>` data=null **)**

Requests a custom spawn, with ``data`` passed to :ref:`_spawn_custom<class_MultiplayerSpawner_method__spawn_custom>` on all peers. Returns the locally spawned node instance already inside the scene tree, and added as a child of the node pointed by :ref:`spawn_path<class_MultiplayerSpawner_property_spawn_path>`.



\ **Note:** Spawnable scenes are spawned automatically. :ref:`spawn<class_MultiplayerSpawner_method_spawn>` is only needed for custom spawns.

.. |virtual| replace:: :abbr:`virtual (This method should typically be overridden by the user to have any effect.)`
.. |const| replace:: :abbr:`const (This method has no side effects. It doesn't modify any of the instance's member variables.)`
.. |vararg| replace:: :abbr:`vararg (This method accepts any number of arguments after the ones described here.)`
.. |constructor| replace:: :abbr:`constructor (This method is used to construct a type.)`
.. |static| replace:: :abbr:`static (This method doesn't need an instance to be called, so it can be called directly using the class name.)`
.. |operator| replace:: :abbr:`operator (This method describes a valid operator to use with this type as left-hand operand.)`
