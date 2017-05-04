---
title: "UnorderedMap::First (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap::First"
ms.assetid: 915e771a-cec1-4905-8ecb-76501f63c143
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMap::First (M&#233;todo)
Devuelve un iterador que especifica el primer elemento [Windows::Foundation::Collections::IKeyValuePair\<K,V\>](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) del objeto UnorderedMap.  
  
## Sintaxis  
  
```cpp  
  
virtual Windows::Foundation::Collections::IIterator<  
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();  
```  
  
## Valor devuelto  
 Un iterador que especifica el primer elemento del mapa.  
  
## Comentarios  
 Una manera cómoda de contener el iterador devuelto por First \(\) es asignar el valor devuelto a una variable que se declare con la palabra clave de deducción de tipos [automática](~/cpp/auto-cpp.md). Por ejemplo: `auto x = myUnorderedMap->First();`.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::UnorderedMap \(Clase\)](../cppcx/platform-collections-unorderedmap-class.md)   
 [Colecciones](../cppcx/collections-c-cx.md)