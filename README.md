# TEE — Open-Source Contributions

**Satellite imagery · Geospatial data · Machine learning · Clustering**

This repository documents contributions I made **as part of a four-person team at Chalmers University of Technology** (DAT300/DIT616, autumn 2026) to [TEE — Tessera Embeddings Explorer](https://github.com/ucam-eo/TEE), an open-source tool for exploring satellite-image embeddings and classifying land cover.

Our work was contributed to the **upstream TEE repository**. This portfolio repository is a summary and link collection, **not a copy or fork of the TEE source code**.

## Contributions merged upstream

| Contribution | What the team worked on | Upstream PR |
| --- | --- | --- |
| **Stable clustering methods** | Added optional approaches to reduce dependence on the k-means seed, including stability-oriented clustering and spatial smoothing; kept standard k-means available as the default. | [#31](https://github.com/ucam-eo/TEE/pull/31) |
| **Polygon rasterization fix** | Fixed an issue where rounding polygon vertices could change pixels along boundaries when exporting and reimporting labels. | [#33](https://github.com/ucam-eo/TEE/pull/33) |
| **Gothenburg sample dataset** | Contributed a labelled land-cover dataset that can be used to explore and evaluate classification workflows in TEE. | [#34](https://github.com/ucam-eo/TEE/pull/34) |

All three pull requests were **merged on 6 November 2026**.

### 1. Clustering stability — PR #31

The original auto-label k-means results could vary significantly with the random seed. The team's contribution introduced optional methods:

- **Stable:** initial over-clustering followed by hierarchical centroid merging and refinement.
- **Stable + smooth:** adds spatial label smoothing.
- **Stable + Gaussian:** smooths the embedding grid before stable clustering.

For the Gothenburg viewport, the PR reports that the share of pixels changing cluster between seeds was reduced from **21.6% to 1.8%** in a comparison described in the pull request.

[Read PR #31 and its evaluation results](https://github.com/ucam-eo/TEE/pull/31)

### 2. Rasterization fix — PR #33

The team identified an export/reimport issue: rounding polygon vertices to pixel corners before rasterization caused differences along polygon boundaries. The accepted change uses the original fractional pixel coordinates to determine which pixel centres fall inside a polygon.

The PR reports **zero gained or lost pixels** in its documented round-trip regression examples after the fix.

[Read PR #33](https://github.com/ucam-eo/TEE/pull/33)

### 3. Gothenburg ground-truth data — PR #34

The contributed `gothenburg.zip` sample dataset describes **2024 land cover** in a 5 km × 5 km area of central Gothenburg.

| Dataset property | Value |
| --- | --- |
| Polygons | **7,483** |
| Classes | **5** |
| Land-cover classes | Street, Buildings, Forest, River, Football field |
| Year | **2024** |
| Labelled coverage | **81%** of the viewport |

The dataset was prepared for evaluating the tool's clustering and classification features and is now available alongside TEE's other sample data.

[Read PR #34](https://github.com/ucam-eo/TEE/pull/34) · [Official worked example](https://github.com/ucam-eo/TEE/blob/main/public/user_guide.md#worked-example-gothenburgzip)

## Team and attribution

The Gothenburg dataset contribution officially credits **Christopher Kröss, Alice Piacentini, Isabel Reguera and Elias Svensson**. The upstream pull requests were opened by Christopher Kröss, and the work described here reflects a **team effort**, not sole authorship.

Upstream project maintainer: [TEE / ucam-eo](https://github.com/ucam-eo/TEE).

## Relevant topics

**Geospatial data · Satellite imagery · Tessera embeddings · K-means · Clustering stability · Polygon rasterization · Testing · Open source**

## Source and further reading

- [TEE — official repository](https://github.com/ucam-eo/TEE)
- [PR #31 — clustering improvements](https://github.com/ucam-eo/TEE/pull/31)
- [PR #33 — rasterization fix](https://github.com/ucam-eo/TEE/pull/33)
- [PR #34 — Gothenburg sample data](https://github.com/ucam-eo/TEE/pull/34)
- [PR #39 — documentation and acknowledgement of the Gothenburg dataset](https://github.com/ucam-eo/TEE/pull/39)

*Portfolio write-up by Alice Piacentini. All source code and datasets remain in their respective upstream repositories under the applicable licenses.*
