---
title: Arrayreference (clase) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ArrayReference::ArrayReference
dev_langs:
- C++
helpviewer_keywords:
- Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7b2a0fd8c4903852e88fa80f12bc05894625888
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42588316"
---
# <a name="platformarrayreference-class"></a>Platform::ArrayReference (Clase)
`ArrayReference` es un tipo de optimización que puedes usar en lugar de [Platform::Array^](../cppcx/platform-array-class.md) en parámetros de entrada cuando desees rellenar una matriz de estilo C con los datos de entrada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
class ArrayReference  
```
  
### <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Arrayreference](#ctor)|Inicializa una nueva instancia de la clase `ArrayReference`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ArrayReference::operator() (Operador)](#operator-call)|Convierte este `ArrayReference` en `Platform::Array<T>^*`.|  
|[ArrayReference::operator= (Operador)](#operator-assign)|Asigna el contenido de otro `ArrayReference` a esta instancia.|  
  
## <a name="exceptions"></a>Excepciones  
  
### <a name="remarks"></a>Comentarios  
 Si usas `ArrayReference` para rellenar una matriz de estilo C, evitas la operación de copia adicional que sería necesaria para copiar primero a una variable `Platform::Array` y después a la matriz de estilo C. Cuando usas `ArrayReference`, solo se realiza una operación de copia. Para obtener un ejemplo de código, vea [Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
### <a name="requirements"></a>Requisitos  
 **Cliente mínimo admitido:** Windows 8  
  
 **Servidor mínimo admitido:** Windows Server 2012  
  
 **Espacio de nombres:** Plataforma  
  
 **Encabezado:** vccorlib.h  
  
## <a name="ctor"></a>  Constructor Arrayreference
Inicializa una nueva instancia de la [Platform:: arrayreference](../cppcx/platform-arrayreference-class.md) clase.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);  
ArrayReference(ArrayReference&& otherArg)  
  
```  
  
### <a name="parameters"></a>Parámetros  
 `dataArg`  
 Puntero a los datos de matriz.  
  
 `sizeArg`  
 Número de elementos de la matriz de origen.  
  
 `otherArg`  
 Objeto `ArrayReference` cuyos datos se moverán para inicializar la nueva instancia.  
  
### <a name="remarks"></a>Comentarios  
  


## <a name="operator-assign"></a>  Arrayreference:: operator = (operador)
Asigna el objeto especificado a la actual [Platform:: arrayreference](../cppcx/platform-arrayreference-class.md) objeto utilizando la semántica de movimiento.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
  
ArrayReference& operator=(ArrayReference&& otherArg);  
  
```  
  
### <a name="parameters"></a>Parámetros  
 `otherArg`  
 Objeto que se mueve al objeto `ArrayReference` actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia a un objeto de tipo `ArrayReference`.  
  
### <a name="remarks"></a>Comentarios  
 `Platform::ArrayReference` es una plantilla de clase estándar de C++, no una clase de referencia.  
  


## <a name="operator-call"></a>  ::Operator() (operador)
Convierte la actual [Platform:: arrayreference](../cppcx/platform-arrayreference-class.md) objeto a un [Platform:: Array](../cppcx/platform-array-class.md) clase.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
  
Array<TArg>^ operator ();  
  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador a objeto de tipo `Array<TArg>^`.  
  
### <a name="remarks"></a>Comentarios  
 [Platform:: arrayreference](../cppcx/platform-arrayreference-class.md) y [Platform:: Array](../cppcx/platform-array-class.md) son clases de plantillas de clase estándares de C++, no ref.  
  


  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)