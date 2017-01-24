---
title: "_variant_t (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Variant"
  - "_variant_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_variant_t (clase)"
  - "_variant_t (clase), funciones miembro"
  - "_variant_t (clase), operadores"
  - "VARIANT (objeto)"
  - "VARIANT (objeto), encapsulación COM"
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _variant_t (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Un objeto `_variant_t` encapsula el tipo de datos `VARIANT`.  La clase administra la asignación y desasignación de recursos, y realiza llamadas a función para **VariantInit** y **VariantClear** según corresponda.  
  
### Construcción  
  
|||  
|-|-|  
|[\_variant\_t](../cpp/variant-t-variant-t.md)|Construye un objeto `_variant_t`.|  
  
### Operaciones  
  
|||  
|-|-|  
|[Attach](../cpp/variant-t-attach.md)|Adjunta un objeto **VARIANT** al objeto `_variant_t`.|  
|[Clear](../cpp/variant-t-clear.md)|Borra el objeto **VARIANT** encapsulado.|  
|[ChangeType](../cpp/variant-t-changetype.md)|Cambia el tipo del objeto `_variant_t` al **VARTYPE** indicado.|  
|[Desasociar](../cpp/variant-t-detach.md)|Desasocia el objeto encapsulado **VARIANT** de este objeto `_variant_t`.|  
|[SetString](../cpp/variant-t-setstring.md)|Asigna una cadena a este objeto `_variant_t`.|  
  
### Operadores  
  
|||  
|-|-|  
|[Operador \=](../cpp/variant-t-operator-equal.md)|Asigna un nuevo valor a un objeto `_variant_t` existente.|  
|[Operador \=\=, \!\=](../cpp/variant-t-relational-operators.md)|Compara dos objetos `_variant_t` para ver si son iguales o no.|  
|[Extractores](../cpp/variant-t-extractors.md)|Extraen datos del objeto **VARIANT** encapsulado.|  
  
## Específicos de Microsoft: END  
  
## Requisitos  
 **Encabezado:** comutil.h  
  
 **Lib:** omsuppw.lib o comsuppwd.lib \(vea [\/Zc:wchar\_t \(wchar\_t es un tipo nativo\)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para obtener más información\)  
  
## Vea también  
 [Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)