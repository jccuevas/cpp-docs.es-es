---
title: ValueType (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ValueType::ToString
dev_langs:
- C++
helpviewer_keywords:
- Platform::ValueType Class
ms.assetid: 79aa8754-b140-4974-a5b1-be046938a10a
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1994aa6445c67bae138a51f1d3eebb2a54f9b17d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="platformvaluetype-class"></a>Platform::ValueType (Clase)
La clase base para las instancias de tipos de valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
public ref class ValueType : Object  
```  
  
## <a name="public-methods"></a>Métodos públicos  
  
|||  
|-|-|  
|[ValueType::ToString](#tostring)|Devuelve una representación de cadena del objeto. Se hereda de [Platform:: Object](../cppcx/platform-object-class.md).|  
  
### <a name="remarks"></a>Comentarios  
 La clase ValueType se usa para construir tipos de valor. ValueType se deriva de Object, que tiene miembros básicos. Sin embargo, el compilador desasocia esos miembros básicos de los tipos de valor que se derivan de la clase ValueType. El compilador vuelve a asociar esos miembros básicos cuando se encuadra un tipo de valor.  
  
### <a name="requirements"></a>Requisitos  
 **Cliente mínimo admitido:** Windows 8  
  
 **Servidor mínimo admitido:** Windows Server 2012  
  
 **Espacio de nombres:** Plataforma  
  
 **Metadatos:** platform.winmd  

## <a name="tostring"></a> ValueType::ToString (método)
Devuelve una representación de cadena del objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
Platform::String ToString();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Platform que representa el valor.  
    
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)