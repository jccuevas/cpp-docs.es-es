---
title: "CComVariant Class | Microsoft Docs"
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
  - "ATL.CComVariant"
  - "ATL::CComVariant"
  - "CComVariant"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComVariant class"
  - "VARIANT macro"
  - "VARIANT macro, ATL"
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
caps.latest.revision: 26
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComVariant Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase envuelve el tipo de `VARIANT` , proporcionando un miembro que indica el tipo de datos almacenados.  
  
## Sintaxis  
  
```  
  
class CComVariant : public tagVARIANT  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComVariant::CComVariant](../Topic/CComVariant::CComVariant.md)|el constructor.|  
|[CComVariant::~CComVariant](../Topic/CComVariant::~CComVariant.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComVariant::Attach](../Topic/CComVariant::Attach.md)|Asocia **VARIANT** al objeto de `CComVariant` .|  
|[CComVariant::ChangeType](../Topic/CComVariant::ChangeType.md)|Convierte el objeto de `CComVariant` un nuevo tipo.|  
|[CComVariant::Clear](../Topic/CComVariant::Clear.md)|borra el objeto de `CComVariant` .|  
|[CComVariant::Copy](../Topic/CComVariant::Copy.md)|Copia **VARIANT** al objeto de `CComVariant` .|  
|[CComVariant::CopyTo](../Topic/CComVariant::CopyTo.md)|Copia el contenido del objeto de `CComVariant` .|  
|[CComVariant::Detach](../Topic/CComVariant::Detach.md)|Desasocia **VARIANT** subyacente del objeto de `CComVariant` .|  
|[CComVariant::GetSize](../Topic/CComVariant::GetSize.md)|Devuelve el tamaño en número de bytes del contenido del objeto de `CComVariant` .|  
|[CComVariant::ReadFromStream](../Topic/CComVariant::ReadFromStream.md)|Carga **VARIANT** de una secuencia.|  
|[CComVariant::SetByRef](../Topic/CComVariant::SetByRef.md)|Inicializa el objeto de `CComVariant` y establezca el miembro de **vt** a **VT\_BYREF**.|  
|[CComVariant::WriteToStream](../Topic/CComVariant::WriteToStream.md)|Guarda **VARIANT** subyacente en una secuencia.|  
  
### Operadores públicos  
  
|||  
|-|-|  
|[CComVariant::operator \<](../Topic/CComVariant::operator%20%3C.md)|Indica si el objeto de `CComVariant` es menor que **VARIANT**especificado.|  
|[CComVariant::operator \>](../Topic/CComVariant::operator%20%3E.md)|indica si el objeto de `CComVariant` es mayor que **VARIANT**especificado.|  
|[el operador\! \=](../Topic/CComVariant::operator%20!=.md)|Indica si el objeto de `CComVariant` no es igual a **VARIANT**especificado.|  
|[operador \=](../Topic/CComVariant::operator%20=.md)|Asigna un valor al objeto de `CComVariant` .|  
|[operator \=\=](../Topic/CComVariant::operator%20==.md)|Indica si el objeto de `CComVariant` es igual a **VARIANT**especificado.|  
  
## Comentarios  
 `CComVariant` contiene el tipo de `VARIANT and VARIANTARG` , que consta de una combinación y miembro que indican el tipo de los datos almacenados en la combinación.  S para**VARIANT**se utiliza normalmente en la automatización.  
  
 `CComVariant` deriva de **VARIANT** junto que puede utilizar dondequiera que **VARIANT** pueda utilizar.  Puede, por ejemplo, utilizar la macro de **V\_VT** para extraer el tipo de `CComVariant` o puede tener acceso al miembro de **vt** directamente igual que las de **VARIANT**.  
  
## Jerarquía de herencia  
 `tagVARIANT`  
  
 `CComVariant`  
  
## Requisitos  
 **encabezado:** atlcomcli.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)