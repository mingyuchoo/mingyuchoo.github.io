---
layout: post
title: "User Story Examples"
date: 2020-05-24 00:00
categories: post
tags: [agile, scrum, userstory]
comments: true
---

## Example 1

```yaml
@tv @wip @manual
Feature: BBC TV Brands Homepage
  As a user of BBC website
  I want to have a web page for every TV brand of the BBC
  So that I can get all the informaiton about my favorite Brand

  Background: Brand is available
    Given: BBC TV brand is available to public or coming soon

  Scenario Outline: TV Brand page
    Given I am on the BBC TV <brand> page
     When the bran page loads
     Then I should see "One iPlayer"
      And I should see clips, galleries, tweeks and related links
      But I should not see "On Radio"

    Examples: List of the TV Brand - Valid
      | brand      |
      | EastEnders |
      | Docker Who |

    Examples: List of the Radio Brands - Invalid
      | brand       |
      | The Archers |
      | Noorin Khan |

```

## Example 2

```yaml
# Id: OCST-1.1.1
# Status: Confirmed
# Service: AWS EC2
# Components:
#   - User Data
# STRIDE:
#   - Elevation of privilege
#   - Informaiton desclosure
# References:
#   - https://docs.aws.amazon.com/AWSEC2/

Feature: User Data contains sensitive information
  As an attacker,
  I want the target to have inappropriately placed sensitive information in User Data that I can access
  In order to obtain sensitive information about the target.

  Scenario Outline: Access via instance attribute
    Given an instance with sensitve information in the User Data attribute
    And a principal with the ability to read the instance attributes
    When the attacker searches the User Data for the "<data-type>"
    Then the sensitive informaiton is returned to the attacker

    Examples: Data types
      | data-type         |
      | passord           |
      | API key           |
      | X.509 private key |
      | SSH private key   |
      | Internal URL      |

  Scenario: Access via CloudFormation
    Given an instance built using CloudFormation
      And a principla with the ability to read CloudFormation templates
     When the attacker searches the CloudFormation templates
     Then the sensitive information is returned to the attacker
```
