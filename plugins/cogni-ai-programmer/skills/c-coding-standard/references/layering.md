# Layering

Layering is the primary technique for reducing complexity in a system. A
system should be divided into layers. Layers should communicate between
adjacent layers using well defined interfaces. When a layer uses a
non-adjacent layer then a layering violation has occurred.

A layering violation simply means we have dependency between layers that
is not controlled by a well defined interface. When one of the layers
changes code could break. We don't want code to break so we want layers
to work only with other adjacent layers.

Sometimes we need to jump layers for performance reasons. This is fine,
but we should know we are doing it and document appropriately.

