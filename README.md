# Robotics Field Guides

Field guides for building, connecting to, and programming real robots.
Published for students at Cal State San Bernardino.

**Live site:** https://csusb-jhbc-cyber-ai-robotics.github.io/robotics-field-guides/

## The guides

| Guide | Covers |
|---|---|
| [Robotics Software Installation](Robotics_Installation_Field_Guide.html) | Ubuntu, toolchain, SSH, robot networking, Python, ROS 2, vendor SDKs, simulation — **start here** |
| [Networking & SSH](Networking_Field_Guide.html) | Addressing, subnetting, routing, DNS, and the CLI diagnostic toolkit |
| [ROS 2](ROS2_Field_Guide.html) | Nodes, topics, services, actions, colcon, launch files, DDS and QoS, TF2, bags |
| [Unitree G1](Unitree_G1_Field_Guide.html) | Network setup, SDK2 over DDS, high- and low-level control, joint indexing, lab safety |
| [Lucky Robots](Lucky_Robots_Field_Guide.html) | Lucky Engine, the Python SDK, Gymnasium training, dataset recording, sim-to-real |

Companion site: **[Coding Fundamentals](https://csusb-jhbc-cyber-ai-robotics.github.io/coding-fundamentals/)**

## Suggested order

1. **Robotics Software Installation** — get a working machine first. Everything
   else assumes the stack it installs.
2. **Networking & SSH** — you cannot reach a robot you cannot address.
3. **ROS 2** — the publish/subscribe model, learned on a laptop with no robot.
4. **Unitree G1** — the hardware, once the concepts are in place.
5. **Lucky Robots** — simulate before deploying to anything with actuators.

## Safety note

The Unitree G1 guide covers a real humanoid robot with real mass and torque. Its
safety chapter and pre-flight checklist are placed before the technical content
deliberately, and the labs are ordered so that nothing moves under power until
several read-only exercises have been completed. Please keep that ordering when
assigning them.

## What these are

Each guide is a **single self-contained HTML file** — no build step, no
dependencies, no external requests. Each carries its own sidebar table of
contents, `Ctrl+K` search across every heading, per-chapter progress tracking,
light/dark themes, and copy buttons on every command block.

Because nothing loads from the network, a student can save one page and read it
offline — which matters in a robotics lab, where the machine you are working on
often has no route to the internet.

## Editing

**Do not edit the HTML in this repo directly.** These files are generated.

The source of truth is the Workipedia vault at `~/Documents/Workipedia`:

- **Networking** is a long-standing vault guide, edited in place.
- **ROS 2**, **Unitree G1**, **Lucky Robots**, and **Robotics Software
  Installation** are built from content modules in `.workipedia/guidekit/guides/`
  via `node .workipedia/guidekit/build.mjs`.

To republish after any change:

```bash
cd ~/Documents/Workipedia/.workipedia/guidekit
node build.mjs        # rebuild generated guides into the vault
node publish.mjs      # copy into both site repos, rewriting cross-site links
node makeindex.mjs    # regenerate the landing pages
node checklinks.mjs ~/Projects/csusb/robotics-field-guides   # verify
```

`publish.mjs` rewrites links on the way out: references to a guide on the
companion Coding Fundamentals site become absolute URLs, and references to
vault-only guides that aren't published here have their links removed but their
text kept.

## Accuracy

Vendor SDKs and simulators move fast. The Unitree G1 and Lucky Robots guides both
open with a warning that specific version numbers, IP addresses, joint indices,
and API signatures should be verified against the hardware and package versions
actually in use. The concepts are stable; the exact numbers are not.

## Hosting

GitHub Pages, served from the repository root on `main`. `.nojekyll` is present
so Jekyll doesn't process the files.
