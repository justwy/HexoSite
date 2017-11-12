---
title: BusTracker Design
date: 2017-11-12 15:11:04
tags:
---

```puml
@startuml

abstract class AbstractList

abstract AbstractCollection

interface List

interface Collection

List <|-- AbstractList
Collection <|-- AbstractCollection
Collection <|- List
AbstractCollection <|- AbstractList
AbstractList <|-- ArrayList

class ArrayList {
  Object[] elementData
  int size()
}

enum TimeUnit {
  DAYS
  HOURS
  MINUTES
}

annotation SuppressWarnings
@enduml
```
