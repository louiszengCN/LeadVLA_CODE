<div align="center">

<h1>LeadVLA: Learning Follower-Aware<br>Route Execution for Robot Leading</h1>

<p><strong>Keep the route. Learn how to adapt.</strong></p>

<p>
Tianle Zeng<sup>1</sup> · Hanjing Ye<sup>1,2</sup> · Bingyi Xia<sup>1</sup> · Yuchen Zhou<sup>2</sup><br>
Zibo Zhang<sup>3</sup> · Yufei Huang<sup>2</sup> · Yonggen Ling<sup>2</sup> · Hong Zhang<sup>1</sup>
</p>

<p>
<sup>1</sup> Southern University of Science and Technology<br>
<sup>2</sup> Tencent Robotics X &nbsp; <sup>3</sup> Futian Laboratory
</p>

<p>
<a href="https://louiszengcn.github.io/LeadVLA_PAGE/"><img src="https://img.shields.io/badge/Project_Page-287D60?style=for-the-badge" alt="Project page"></a>
<a href="https://louiszengcn.github.io/LeadVLA_PAGE/#teaser"><img src="https://img.shields.io/badge/Video_Demos-30343B?style=for-the-badge" alt="Video demos"></a>
<a href="#release-roadmap"><img src="https://img.shields.io/badge/Release_Roadmap-30343B?style=for-the-badge" alt="Release roadmap"></a>
</p>

<p><a href="#overview">Overview</a> · <a href="#demos">Demos</a> · <a href="#method">Method</a> · <a href="#leadinfra--leadbench">LeadInfra &amp; LeadBench</a> · <a href="#citation">Citation</a></p>

</div>

> **Release status:** This repository currently contains the project overview and visual materials. We will progressively open-source model checkpoints, training code, LeadInfra, and LeadBench. See the [release roadmap](#release-roadmap) for planned deliverables. The arXiv link and BibTeX will be added once the preprint is available.

## Overview

**LeadVLA** is a vision-language-action policy for **follower-aware robot leading**. Given a planned route and a language instruction identifying whom to lead, the robot adapts its pace and local motion to the designated follower and the surrounding scene.

The project brings together three components:

| Component | Role |
| :--- | :--- |
| **LeadVLA** | A policy that combines a given **Path** with learned **Pace** and **Residual** to produce follower-aware robot motion. |
| **LeadInfra** | A simulation and data-generation infrastructure for diverse, closed-loop robot-leading interactions. |
| **LeadBench** | A closed-loop benchmark that measures route completion together with responsiveness to the designated follower. |

## Demos

Real-world robot leading in a coffee shop and an airport terminal. **Click a preview to explore the videos on our project page.**

<table>
  <tr>
    <td align="center" width="50%">
      <a href="https://louiszengcn.github.io/LeadVLA_PAGE/#real-world"><img src="assets/images/real-coffee.webp" alt="Coffee shop demo: front and rear camera views, route visualization, and third-person view" width="440"></a><br>
      <strong>Coffee shop</strong><br>
      Adapting to a customer's movement along the route.
    </td>
    <td align="center" width="50%">
      <a href="https://louiszengcn.github.io/LeadVLA_PAGE/#real-world"><img src="assets/images/real-terminal.webp" alt="Airport terminal demo: a robot guides a designated traveler" width="440"></a><br>
      <strong>Airport terminal</strong><br>
      Guiding a designated traveler to the departure area.
    </td>
  </tr>
</table>

<p align="center"><a href="https://louiszengcn.github.io/LeadVLA_PAGE/#teaser"><strong>▶ Watch the overview video</strong></a> &nbsp; · &nbsp; <a href="https://louiszengcn.github.io/LeadVLA_PAGE/#leadinfra">Explore simulation scenarios</a></p>

## Method

<p align="center">
  <img src="assets/images/method.webp" alt="LeadVLA architecture: front and rear RGB histories, an instruction, and a global route feed a VLM backbone; shared action queries predict Pace and Residual, and a Path Composer generates final waypoints" width="100%">
</p>

LeadVLA processes front- and rear-view RGB history, the instruction, and route context in one multimodal forward pass. Its structured action representation separates three roles:

- **Path — where to go.** The planned route provides a stable guide.
- **Pace — how to progress.** Learned route-progress scaling lets the robot slow down, stop, resume, or speed up with the follower.
- **Residual — how to adjust locally.** Learned corrections adapt the paced route to the follower and nearby scene changes.

A deterministic **Path Composer** combines the given route with the predicted Pace and Residual to produce the final robot-local waypoints.

## LeadInfra & LeadBench

<p align="center">
  <img src="assets/images/leadinfra-assets.webp" alt="LeadInfra scene assets, human appearances, robot platforms, and static obstacles" width="100%">
</p>

**LeadInfra** composes scenes, routes, robot embodiments, follower behaviors, formations, and distractors into closed-loop interactions. The infrastructure supports diverse robot-leading scenarios and supervision generated from how each interaction unfolds.

**LeadBench** evaluates robot leading across **Core, Easy, and Constrained** settings with both **single-person and multi-person** scenarios. It tests whether a policy can follow the route while continuing to respond to the designated follower.

<p align="center"><a href="https://louiszengcn.github.io/LeadVLA_PAGE/#leadinfra">Explore LeadInfra</a> &nbsp; · &nbsp; <a href="https://louiszengcn.github.io/LeadVLA_PAGE/#leadbench">Explore LeadBench</a> &nbsp; · &nbsp; <a href="https://louiszengcn.github.io/LeadVLA_PAGE/#results">View paper results</a></p>

## Release Roadmap

We plan to open-source the project in stages. **All implementation and model releases below are upcoming**; this initial repository provides an overview and demo previews.

| Stage | Planned release | Planned contents | Status |
| :---: | :--- | :--- | :---: |
| 1 | **Model checkpoints** | LeadVLA weights, model-loading instructions, and an inference example. | ⏳ Planned |
| 2 | **Training code** | Training pipeline, configurations, and data-preparation instructions. | ⏳ Planned |
| 3 | **LeadInfra** | Simulation and data-generation tools, scenario configuration, and setup documentation. | ⏳ Planned |
| 4 | **LeadBench** | Benchmark definitions, evaluation tools, metrics, and evaluation instructions. | ⏳ Planned |

Download links and usage documentation will be added here as each component becomes available. Release dates are not yet announced; the order and scope may be refined as we prepare the releases.

## Citation

If you find LeadVLA useful for your research, please consider citing our paper. The **arXiv link and BibTeX entry are coming soon** and will be added here after the preprint is published.
