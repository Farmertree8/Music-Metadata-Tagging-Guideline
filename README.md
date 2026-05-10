# Music Metadata Tagging Guideline

Music listening tracking websites such as Last.fm have gradually flourished alongside the growth of the Internet. However, their metadata originates from different music platforms, resulting in inconsistent content, formats, and filtering standards without any unified specification. Although many existing filters provide built-in or user-defined post-processing features, slight implementation differences still lead to conflicts between multiple rule sets (see xkcd 927).

These guidelines are proposed to address this issue.

- [繁體中文](README.zh.md)
- [English](README.md)

# Core Principles

Rules are applied from top to bottom in descending order of importance:

> `0. Formatting Principles`
> `1. Respect Original Formatting`
> `2. Preserve Original Text`
> `3. Correct Attribution`
> `4. Ignore Annotations`
> `5. Follow Conventions`

## 0. Formatting Principles

1. Use UTF-8 encoded metadata.
2. Filenames and notation should follow the format `Artist - Title`, where the separator `-` consists of:
    - space
    - hyphen (minus sign)
    - space

## 1. Respect the Author

When an author uploads metadata using a specific formatting style for artist names or titles, every effort should be made to preserve that formatting while minimizing removed content, except for the removable parts listed later.

Reliability should be determined in the following descending order:

1. Official release metadata
2. Metadata from audio uploaded by the original author
3. YouTube auto-generated copyright audio metadata
4. Metadata from platforms such as YouTube Music or Spotify
5. Metadata stored in community databases
6. Metadata from reuploads

The same principles apply to album names and album artists, although these may be left blank if uncertain.

### Avoid Excessive Assumptions

- For smaller creators or uploads that appear to be demos/prototypes, directly assume the video title is the track title.
- The same principle applies to meme remixes or MAD videos; their upload channel and video title should be treated as the tagged artist and track title.

## 2. Preserve Original Text

1. For non-English tagged artists, preserve the original language, symbols, and formatting whenever possible (except where filename limitations apply).
   - ❌`Kurokotei`, ❌`Kurokotei / 黒皇帝`, ❌`黑皇帝`, ✅`黒皇帝`
   - ❌`Curren`, ❌`icesawder`, ❌`.。*°+.*.Curren。+..。*°+`, ✅`.｡*ﾟ+.*.Curren｡+..｡*ﾟ+`

2. Do not replace originally joined tagged artists with commas or semicolons unless the author explicitly uses them.
    - ❌`Betwixt, Between`, ❌`Betwixt; Between`, ✅`Betwixt & Between`
    - This issue is especially common with simplified preprocessing on streaming platforms such as Spotify, and can often be avoided through local backups.

3. Multiple tagged artists should follow the author’s original notation, since the meaning may differ significantly.
    - Example: `PIKASONIC & Tatsunoshin - Shizuku (ft. NEONA & KOTONOHOUSE)`
    - Composer(s): `PIKASONIC & Tatsunoshin`
    - Title: `Shizuku (ft. NEONA & KOTONOHOUSE)`
    - Not: 
       - `PIKASONIC & Tatsunoshin, NEONA & KOTONOHOUSE` and `Shizuku` nor
       - `PIKASONIC, Tatsunoshin, NEONA, KOTONOHOUSE` and `Shizuku (ft. NEONA & KOTONOHOUSE)`

4. Vocaloids should not be treated as another tagged artists unless explicitly formatted that way by the creator.
    - `r-906 - 匙ノ咒 / 初音ミク`
    - Tagged as:
       - Artist: `r-906`
       - Title: `匙ノ咒`

5. Even if multiple names are aliases of the same person, preserve and display them in their original combined format.
    - `XH, KYURO3, YUTRAZIUM`, actual composer: `XH`
    - `Kobaryo & Matatabi Sound System + DJ NECOJITA + Shinonome I`, actual composer: `Kobaryo`
    - However, if the original author only mentions aliases in the title, they should generally be ignored.

### Tagged Artist Priority

Music production often involves multiple contributors and fictional characters. If the author does not explicitly specify attribution, select the tagged artist using the following descending priority order:
1. `Arranger`
2. `Composer`
3. `Producer`
4. `Vocalist`
5. `Circle`

> Additionally:
> - `Alias` refers to alternate names or pseudonyms of the composer.
> - Handling is described in point 5 above.

## 3. Correct Attribution

The following are common causes of incorrect metadata and should be corrected or removed after import:

1. Remixes and other derivative works should tag **only the remixer** as the sole tagged artist.
2. Many channels include suffixes such as:
    - ` - Topic`
    - ` Official`
    - `VEVO`
3. Some channel names may differ slightly from the correct tagged artist:
    -  `Sliver's Castle` should be `AIKA`
    - `かんざきひろ / Kanzaki Hiro` should be `Hiroyuki ODA`
4. Work titles or album names should not be used as tagged artists:
    - `Touhou - `
    - `Minecraft OST`
    - `All of Human History`
5. Music genres should not be used as tagged artists.
    - Depending on context, they may remain in the title.
    - Example: `Nightcore - Israeli Teufelslied`
       `Nightcore` may remain as part of the title.
6. Some uploads wrap the actual title in quotation marks or brackets that should be removed.
    - `VIviα - 『君がいた照明』`
    - Correct form: `VIviα - 君がいた照明`

## 4. Ignore Annotations

Here, “annotations” refers to supplementary information that is not part of the official work title or tagged artist, but instead describes the video, release, platform, genre, media format, or usage context.

Uploaded music sources often contain additional context to help viewers understand the track background, but such information usually makes metadata noisy and inaccurate, so it should generally be removed.

### Maximize Annotation Removal

Annotations that do not significantly affect the music itself should be removed whenever possible. The following are common but non-exhaustive examples of unnecessary information:

1. Video formats
    - `(Music Video)`
    - `(Visualizer)`

2. Official status
    - `(Official Video)`
    - `(Unofficial Upload)`

3. Music genres
    - `[Frenchcore]`
    - `[Trance]`

4. Music state/version descriptors
    - `(Long Version)`
    - `(Instrumental)`
    - However, remix/version identifiers such as the following should be preserved:
      - `(VIP Edit)`
      - `(Camellia Bootleg)`
      - `(Game Ver.)`

5. Usage contexts
    - `【maimai でらっくす】`
    - `「Punishing: Gray Raven OST - 遥岸方舟」`

6. Included albums
    - `[Phant 3]`
    - `【Awakening EP】`

7. Release events
    - `【#RDB2024-R2】`
    - `【C94 Electronica⧸Trance】`

8. Upload channel branding
    - `NCS - Copyright Free Music`

9. Placeholder separators or symbols
    - ` / `
    - ` | `
    - extra whitespaces

## 5. Follow Conventions

If none of the above rules apply, search and infer metadata according to the reliability order defined in Principle 1. Only afterward should long-established naming conventions from websites such as Last.fm be considered as references.

Similar exceptions should also be handled using the **same processing logic**.

## Inspiration

- [sparanoid/chinese-copywriting-guidelines](https://github.com/sparanoid/chinese-copywriting-guidelines)
