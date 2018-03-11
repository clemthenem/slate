---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:

includes:
  - authentication
  - users
  - account_confirmation
  - account_identities
  - account_verifications
  - tutor_profile
  - profile_translations
  - competences
  - price_listings
  - price_listing_sets
  - general
  - errors

search: true
---

# Introduction

Welcome to the Tutory API! 

This document describes the Tutory v1 API, which is meant to be used by back-end servers or trusted parties performing administrative tasks. Create a new booking, read user profile and reviews data, and more.

Generally speaking, anything that can be done through the Tutory dashboard (and more) can also be done through this API.

All requests should be send to `tutory.com.au`

## JSON API

The Tutory API requests and responses are using the JSON API format. 

It is a specification for how a client should request that resources be fetched or modified, and how a server should respond to those requests.

JSON API requires use of the JSON API media type `application/vnd.api+json` for exchanging data.


