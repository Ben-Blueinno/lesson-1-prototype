# Lesson 1 Prototype - GoDot Game Development

![Alt Text](lesson-1-prototype-demo.gif)

## Project Overview

This project is a prototype for Lesson 1 of a GoDot Game Development course. It introduces basic concepts of game development using the GoDot engine.

## Lesson Flow

### Stage 1: Introduction to godot/game-dev

### Stage 2: Installation

**Remark:** May install godot editor from the mirrored v4.3 [Google Drive Link](https://drive.google.com/drive/folders/1z_dHyR1U2pg-ClmWM2k2Rb_7sJIUACvj?usp=sharing)

### Stage 3: Material Distribution

**Tasks:**

- Distribute the GitHub Classroom link to students
- Guide students to import the class project into Godot

### Stage 4: Godot Basics

**Tasks:**

- Run the game window, select the "MainScene" node and run (empty scene)

**Changes:**

```yaml
stage 4:
  changes:
    root node (3D Scene):
      name: MainScene
```

### Stage 5: Introduce node system

**Tasks:**

- Create a box as ground, add objects on the ground as a 3D scene
- Sample [bruno-simon.com](https://bruno-simon.com)
- Expected some basic 3D objects (e.g. box, sphere, cylinder)

**Changes:**

```yaml
stage 5:
  changes:
    MainScene:
      - MeshInstance3D:
          name: Ground
          mesh:
            type: New Box Mesh
            mesh size: (100, 2, 100)
          transform:
            position: (0, -1, 0)
          children:
            - MeshInstance3D:
                name: Tree
                mesh:
                  type: New Cylinder Mesh
                  top radius: 0.8
                  bottom radius: 1
                  height: 10
                  material:
                    type: New StandardMaterial3D
                    albedo:
                      color: brown (#8B4513)
                transform:
                  position: (0, 5, 0)
                children:
                  - MeshInstance3D:
                      name: Leaf
                      mesh:
                        type: New Sphere Mesh
                        radius: 4
                        height: 10
                        material:
                          type: New StandardMaterial3D
                          albedo:
                            color: green (#008000)
                      transform:
                        position: (0, 5, 0)
```

### Stage 6: Basic 3D objects/meshes

**Tasks:**

- Create 3D camera (static) and add to the scene
- Add a directional light to the scene
- Add environment to the scene
- Run the game window

**Changes:**

```yaml
stage 6:
  changes:
    MainScene:
      - Camera3D:
          name: MainCamera
          transform:
            position: (0, 20, 25)
            rotation: (-20, 0, 0)
      - DirectionalLight3D
      - WorldEnvironment
```

### Stage 7: Characteristics of different 3D Bodies

**Tasks:**

- Explain the differences between StaticBody3D and RigidBody3D [YouTube Link](https://youtu.be/xp37Hz1t1Q8)
- Add a StaticBody3D node to the scene
- Add a RigidBody3D node to the scene
- Expected a scene with a static body and a dynamic body, like a ball dropping on the ground and stay there

**Changes:**

```yaml
stage 7:
  changes:
    MainScene:
      - Ground:
          children:
            - StaticBody3D:
                children:
                  - CollisionShape3D
      - Tree:
          children:
            - StaticBody3D:
                children:
                  - CollisionShape3D
            - Leaf:
                children:
                  - StaticBody3D:
                      children:
                        - CollisionShape3D
      - RigidBody3D:
          name: Ball
          transform:
            position: (2, 30, 0)
          children:
            - CSGShere3D:
                radius: 2
                radial segment: 100
                rings: 100
                material:
                  type: New StandardMaterial3D
                  albedo:
                    color: orange (#FFA500)
            - CollisionShape3D:
                shape:
                  type: SphereShape3D
                  radius: 2
```

### Stage 8: Duplicating nodes

**Tasks:**

- Save the tree object as a scene
- Save the ball object as a scene
- Duplicate the tree object and place it somewhere else
- Duplicate the ball object and place it somewhere else

**Changes:**

```yaml
stage 8:
  changes:
    MainScene:
      - Tree:
          name: TreeScene
      - Ball:
          name: BallScene
      - Tree1:
          transform:
            position: any
      - Tree2:
          transform:
            position: any
      - Tree3:
          transform:
            position: any
      - Tree4:
          transform:
            position: any
      - Ball1:
          transform:
            position: any
      - Ball2:
          transform:
            position: any
```

## Additional Resources

- [Lesson Flow](lesson_flow.yaml)
- [Demo Video](lesson-1-prototype-demo.avi)
