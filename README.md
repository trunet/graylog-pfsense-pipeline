pfSense Graylog Pipeline Rules
================================

[![License: GPL](https://img.shields.io/badge/License-GPL-blue.svg)](https://www.gnu.org/licenses/gpl.html)

This repository contains [pfSense](https://www.pfsense.org/) related [graylog](https://www.graylog.org/) pipeline rules.

Graylog doesn't support pipeline in content packs yet, in the future this will become a content pack. [#4222](https://github.com/Graylog2/graylog2-server/issues/4222)

## Getting Started

### Create a new stream

Example:

* Field source must match exactly pfsense
* Field application_name must match exactly filterlog

### Create the pipeline rules

* System/Pipelines/Manage rules
* Copy/paste this repository txt files one on each rule

### Create the pipeline

* System/Pipelines/Manage pipelines/Add a new pipeline
* Edit connections and select the stream you created
* Edit stage 0 and add all pfsense rules you created

## Additional scripts

`generate_fields_from_csv.awk` will help you to generate new rules based on CSV extractor rules

Example

```
$ echo "RuleNumber,SubRuleNumber,Anchor,Tracker,Interface,Reason,Action,Direction,IPVersion,Class,FlowLabel,HopLimit,Protocol,ProtocolID,Length,SourceIP,DestIP,SourcePort,DestPort,DataLength" | ./generate_fields_from_csv.awk 
  set_field("RuleNumber", m[0]);
  set_field("SubRuleNumber", m[1]);
  set_field("Anchor", m[2]);
  set_field("Tracker", m[3]);
  set_field("Interface", m[4]);
  set_field("Reason", m[5]);
  set_field("Action", m[6]);
  set_field("Direction", m[7]);
  set_field("IPVersion", m[8]);
  set_field("Class", m[9]);
  set_field("FlowLabel", m[10]);
  set_field("HopLimit", m[11]);
  set_field("Protocol", m[12]);
  set_field("ProtocolID", m[13]);
  set_field("Length", m[14]);
  set_field("SourceIP", m[15]);
  set_field("DestIP", m[16]);
  set_field("SourcePort", m[17]);
  set_field("DestPort", m[18]);
  set_field("DataLength", m[19]);
```

## Authors

* **Wagner Sartori Junior** - *Initial work* - [trunet](https://github.com/trunet)

## License

This project is licensed under the GPL License - see the [COPYING.md](COPYING.md) file for details
