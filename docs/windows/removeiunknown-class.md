---
title: "RemoveIUnknown (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::Details::RemoveIUnknown"
dev_langs: 
  - "C++"
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RemoveIUnknown (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
template <  
   typename T  
>  
struct RemoveIUnknown;  
  
template <  
   typename T  
>  
class RemoveIUnknown : public T;  
```  
  
#### Parámetros  
 `T`  
 Una clase.  
  
## Comentarios  
 Haga un tipo que es equivalente a `IUnknown`\- el tipo basado, pero tiene `QueryInterface`no virtual, `AddRef`, y el miembro de `Release` funciona.  
  
 De forma predeterminada, los métodos COM proporcionan `QueryInterface`virtual, `AddRef`, y métodos release.  Sin embargo, `ComPtr` no requiere la sobrecarga de métodos virtuales.  `RemoveIUnknown` elimina esa sobrecarga proporcionando private, a `QueryInterface`no virtual, a `AddRef`, y métodos de `Release` .  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`ReturnType`|Un sinónimo de un tipo que es equivalente al parámetro `T` de plantilla pero tiene miembros no virtual IUnknown.|  
  
## Jerarquía de herencia  
 `T`  
  
 `RemoveIUnknown`  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)