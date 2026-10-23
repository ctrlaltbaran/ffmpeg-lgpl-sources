# ffmpeg LGPL source

Corresponding source for the `ffmpeg` and `ffprobe` programs shipped with an application, offered
under the GNU Lesser General Public License.

The programs are **FFmpeg n8.1.3** (commit `1041abdc962f4cc4f394aa8de9dc5236c0c3b9e7`), built as
LGPL version 3 (never GPL, never "nonfree") with shared libraries, no network support, and the
AAC, H.264, HEVC and VVC codecs removed. **LAME** (MP3, LGPL 2.0 or later) is linked statically into
`libavcodec`. The other libraries are Opus, Vorbis, Ogg, libvpx, libaom, SVT-AV1, dav1d, libwebp,
zlib and xz (liblzma), all under permissive licences.

## What is here

Each release holds one source bundle per platform (`linux64`, `linuxarm64`, `win64`, `winarm64`)
and a `SHA256SUMS` file. Use the release that matches the programs you have:

- **`rev5`** (current): the builds with the Dolby/DTS audio, speech and proprietary audio, and
  professional video decoders removed. Its bundles are `ffmpeg-<platform>-8.1.3-fileforge5-source.tar`.
- **`rev4`**: the earlier builds, with those decoders still in. Its bundles are
  `ffmpeg-<platform>-8.1.3-fileforge4-source.tar`.

Each bundle's `REBUILD.txt` says how to rebuild it and what the removed decoders are. Each `…-source.tar` contains:

- `ffmpeg-n8.1.3.tar.xz`: FFmpeg's source at that tag;
- `lame-r6835.tar.xz`: LAME's full source (SVN revision 6835);
- `btbn-ffmpeg-builds-*.tar.xz`: the BtbN/FFmpeg-Builds recipe at the pinned commit, which names the
  exact commit of every other library and builds the container images;
- `scripts/`: the build script, the configure line (`flags.sh`), the library list
  (`dependencies.txt`) and licence checks;
- `licenses/`: the licence texts of FFmpeg and every library;
- `BUILD.txt` (the exact configure line and versions) and `REBUILD.txt` (how to rebuild and relink).

To rebuild, or to relink against your own version of a library, follow `REBUILD.txt` inside the
bundle. The libraries are shared (`lib/` next to the program, or the DLLs on Windows), so you can
also replace them with ones you built. Rebuilding needs podman or docker, git, a network connection
and about 6 GB of disk.

Check a download with `sha256sum -c SHA256SUMS`.

## Questions

Open an issue in this repository.

This repository is not affiliated with or endorsed by the FFmpeg project.
FFmpeg is a trademark of Fabrice Bellard.
