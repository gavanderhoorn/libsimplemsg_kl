# libsimplemsg_kl

## Overview

This is an implementation of the ROS-Industrial [Simple Message][] protocol in
Fanuc Karel. Intended mainly for use with the ROS nodes in [fanuc_driver][], it
can be used stand-alone as well (to implement a custom RPC protocol for
instance, see also [genfrkl][]).


## Supported Messages

This library includes support for the `PING`, `GET_VERSION`, `JOINT_POSITION`,
`JOINT_TRAJ_PT`, `STATUS`, `JOINT_TRAJ_PT_FULL` and `JOINT_FEEDBACK` message
structures. Note that not all message libraries implement both serialisation
and deserialisation routines: depending on the way the messages are typically
used (ie: sent or received by the controller) only one direction may be
supported.


## Naming

As Karel imposes severe restrictions on identifier name length (12 characters
max), message libraries and type (`.th.kl`) and routine prototype (`.h.kl`)
header names include the message's assigned identifiers only (and in
hexadecimal).

As an example, the assigned identifier for `JOINT_TRAJ_PT_FULL` is `14`, or
`E` in hexadecimal. The main message structure is then `sm000E_t`, with related
routines prefixed with `sm000E_` and files also following this convention
(`libsm000E.kl`, etc). Refer to [REP-I0004][] for the list of currently
assigned message identifiers.


## Building and Usage

This package is a [rossum][] package and is ideally build with that. Package
build dependencies are listed in the package manifest. For usage without
`rossum` see the [backwards compatibility][] entry in the [ktransw][] FAQ.
See [rossum][] also for more information on how to build a `rossum` workspace.

To use the individual message libraries just include the relevant headers (both
type and routine prototype). Then call the declared routines with the
appropriate arguments.



[Simple Message]: http://wiki.ros.org/simple_message
[fanuc_driver]: http://wiki.ros.org/fanuc_driver
[genfrkl]: https://github.com/gavanderhoorn/genfrkl
[REP-I0004]: https://github.com/ros-industrial/rep/blob/master/rep-I0004.rst
[rossum]: https://github.com/gavanderhoorn/rossum
[backwards compatibility]: https://github.com/gavanderhoorn/ktransw_py#how-about-backwards-compatibility-with-non-ktransw-users
[ktransw]: https://github.com/gavanderhoorn/ktransw_py
