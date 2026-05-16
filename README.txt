LICENSE:
  The build script are all under GPL v2

OVERVIEW:
  This generates the VTless live images

  There are no desktops installed on this ISO, except for a minimal Weston to demonstrate vtty-launch and uvtty-launch

  This ISO cannot be installed easily as Calamares is not on this ISO as this ISO is meant to be a small demonstration of VT-less OSes with no desktops

  These scripts all came from RBOS

  This is likely not going to be maintained much in the future, as it is just a demo of ReterminateVT 
  
BUILDING:
  Run
  vtless_builder.sh
  and press enter two times. It makes two chroots under 
  /var/cache/VTLESS_Build_Files/
  and places the ISO as
  ~/VTless/VTless_${BUILDARCH}.iso
  Usually  ~/VTless/VTless_amd64.iso

  CONTROL FILES (relative to /var/cache/VTless_Build_Files):
        DontDownloadDebootstrapScript:                  Delete this file to force the downloaded debootstrap in VTLESS_Build_Files to run again at the
                                                        next build
        DontRestartArchivesamd64:                       Delete this file to force all the downloaded packages to be downloaded again for the 
                                                        respective architecture.
        DontRestartSourceDownloadamd64:                 Delete this file to force all the downloaded source repositories to be downloaded again for
                                                        the respective architecture.
        DontRestartPhase1amd64:                         Delete this file to force Phase1 to debootstrap again for the respective architecture. This
                                                        only hosts the smaller chroot system that downloads everything
        DontRestartPhase2amd64:                         Delete this file to force Phase2 to debootstrap again for the respective architecture. This
                                                        is the chroot that gets copied to Phase3, and is on the output ISO files.
        DontRestartBuildoutputamd64:                    Delete this file to force all deb packages to rebuild for the respective architecture. This
                                                        will increase the build time.
        DontRestartRustDownloadamd64:                   Delete this file to force build_core to re-download Rust
        DontStartFromScratchamd64:                      Delete this file to force delete everything included downloaded repositories for the
                                                        respective architecture, and cause it to start from scratch.
        DontRestartCargoDownloadamd64:                  Clear the Cargo cache
        DontRestartRustDownloadamd64:                   Force build_core to download a new build of Rust
        build/amd64/buildoutput/control/(packagename):  Delete these files to specify a specific package to rebuild.
        buildcore_revisions_amd64.txt:                  Add a revisions file into this path, to specify particular packages, as described above
        RestartPackageList_amd64.txt:                   Add in the list of packages (as in the files in build/amd64/buildoutput/control/ ).
                                                        One per each line. For batch resetting particular packages
        DontForceSnapshotBuildamd64:                    Delete this file only after the first run is complete, before the next build. This forces
                                                        temporary chroots to be built
USING:
  The ISO can be used in a VM

  It doesn't have an installer as Calamares would inflate the size of the ISO with a Qt dependency

  ReterminateVT is installed.
        Basics are, 

           Use Ctrl+Alt+Shift+Esc to start a new session on the seat if a user is logged in

           A minimal Weston is provided so that it is possible to demonstrate `vtty-launch weston`

           uvtty-session can also be run from vtty-launch. This simulates starting uvtty's the same way a login manager otherwise would.
           uvtty-launch works from here.
