Object Detection
=======

This directory contains development and testing scripts for object detection
in point clouds.


Object Detection Technique Comparison
==================

To compare detection techniques, we define a generic `Model Detector` from which comparable
techniques derive, which performs object detection given a model.

It consumes, from a YAML file:
  - [Mandatory] "points": A pointcloud, as a path to a PCD file.
  - [Mandatory] A list of model URDFs, as paths to URDF files.
  - [Optional] An initial guess for the detector, in the form of a position vector
    for the supplied set of models.

It produces, as a YAML file:
  - A list of ("pose", "score") pairs of model pose hypotheses.