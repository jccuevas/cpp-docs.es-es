---
title: InterfaceListHelper (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::InterfaceListHelper
dev_langs: C++
helpviewer_keywords: InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4465a380d24cbb9607785e958a88801c5de68b15
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="interfacelisthelper-structure"></a>InterfaceListHelper (estructura)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <  
   typename T0,  
   typename T1 = Nil,  
   typename T2 = Nil,  
   typename T3 = Nil,  
   typename T4 = Nil,  
   typename T5 = Nil,  
   typename T6 = Nil,  
   typename T7 = Nil,  
   typename T8 = Nil,  
   typename T9 = Nil  
>  
struct InterfaceListHelper;  
  
template <  
   typename T0  
>  
struct InterfaceListHelper<T0, Nil, Nil, Nil, Nil, Nil, Nil, Nil, Nil>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T0`  
 Parámetro de plantilla 0, lo que es necesario.  
  
 `T1`  
 Parámetro de plantilla 1, que no se especifica de forma predeterminada.  
  
 `T2`  
 Parámetro de plantilla 2, que no se especifica de forma predeterminada. El tercer parámetro de plantilla.  
  
 `T3`  
 Parámetro de plantilla 3, que no se especifica de forma predeterminada.  
  
 `T4`  
 Parámetro de plantilla 4, que no se especifica de forma predeterminada.  
  
 `T5`  
 Parámetro de plantilla 5, que no se especifica de forma predeterminada.  
  
 `T6`  
 Parámetro de plantilla 6, que no se especifica de forma predeterminada.  
  
 `T7`  
 Parámetro de plantilla 7, que no se especifica de forma predeterminada.  
  
 `T8`  
 Parámetro de plantilla 8, que no se especifica de forma predeterminada.  
  
 `T9`  
 Parámetro de plantilla 9, que no se especifica de forma predeterminada.  
  
## <a name="remarks"></a>Comentarios  
 Crea un tipo de InterfaceList aplicar los argumentos de parámetro de plantilla especificada de forma recursiva.  
  
 La plantilla de InterfaceListHelper utiliza el parámetro de plantilla `T0` para definir los primeros datos de miembro en un InterfaceList (estructura) y, a continuación, de forma recursiva aplica la plantilla de InterfaceListHelper a los restantes parámetros de plantilla. InterfaceListHelper se detiene cuando no hay ningún parámetro de plantilla restantes.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`TypeT`|Un sinónimo del tipo InterfaceList.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `InterfaceListHelper`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)