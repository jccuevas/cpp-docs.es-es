---
title: Clase CComSafeArrayBound | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::GetCount
- ATLSAFE/ATL::GetLowerBound
- ATLSAFE/ATL::GetUpperBound
- ATLSAFE/ATL::SetCount
- ATLSAFE/ATL::SetLowerBound
dev_langs:
- C++
helpviewer_keywords:
- CComSafeArrayBound class
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 1cc2adef85c902b7ad12b152b35a7ef68e6abacb
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="ccomsafearraybound-class"></a>Clase CComSafeArrayBound
Esta clase es un contenedor para una [SAFEARRAYBOUND](http://msdn.microsoft.com/en-us/303a9bdb-71d6-4f14-8747-84cf84936c6d) estructura.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComSafeArrayBound : public SAFEARRAYBOUND
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[CComSafeArrayBound](#ccomsafearraybound)|El constructor.|  
|[GetCount](#getcount)|Llame a este método para devolver el número de elementos.|  
|[GetLowerBound](#getlowerbound)|Llame a este método para devolver el límite inferior.|  
|[GetUpperBound](#getupperbound)|Llame a este método para devolver el límite superior.|  
|[SetCount](#setcount)|Llame a este método para establecer el número de elementos.|  
|[SetLowerBound](#setlowerbound)|Llame a este método para establecer el límite inferior.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operador =](#operator_eq)|Establece el `CComSafeArrayBound` en un nuevo valor.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase es un contenedor para la **SAFEARRAYBOUND** estructura utilizada por [CComSafeArray](../../atl/reference/ccomsafearray-class.md). Proporciona métodos para consultar y establecer los límites superiores e inferiores de una sola dimensión de un `CComSafeArray` objeto y el número de elementos que contiene. Multidimensional `CComSafeArray` objeto utiliza una matriz de `CComSafeArrayBound` objetos, uno para cada dimensión. Por lo tanto, cuando se usan métodos como [GetCount](#getcount), tenga en cuenta que este método no devolverá el número total de elementos de una matriz multidimensional.  
  
 **Encabezado:** atlsafe.h  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsafe.h  
  
##  <a name="ccomsafearraybound"></a>CComSafeArrayBound::CComSafeArrayBound  
 El constructor.  
  
```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `ulCount`  
 Número de elementos de la matriz.  
  
 `lLowerBound`  
 El límite inferior desde la que se numera la matriz.  
  
### <a name="remarks"></a>Comentarios  
 Si la matriz es tener acceso desde un programa de Visual C++, se recomienda que el límite inferior se define como 0. Es preferible utilizar un valor de límite inferior diferente si la matriz es para su uso con otros lenguajes, como Visual Basic.  
  
##  <a name="getcount"></a>CComSafeArrayBound::GetCount  
 Llame a este método para devolver el número de elementos.  
  
```
ULONG GetCount() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de elementos.  
  
### <a name="remarks"></a>Comentarios  
 Si el asociado `CComSafeArray` objeto representa una matriz multidimensional, este método sólo devolverá el número total de elementos en la dimensión del extremo derecho. Utilice [CComSafeArray::GetCount](../../atl/reference/ccomsafearray-class.md#getcount) para obtener el número total de elementos.  
  
##  <a name="getlowerbound"></a>CComSafeArrayBound::GetLowerBound  
 Llame a este método para devolver el límite inferior.  
  
```
LONG GetLowerBound() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el límite inferior de la `CComSafeArrayBound` objeto.  
  
##  <a name="getupperbound"></a>CComSafeArrayBound::GetUpperBound  
 Llame a este método para devolver el límite superior.  
  
```
LONG GetUpperBound() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el límite superior de la `CComSafeArrayBound` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El límite superior depende del número de elementos y el valor de límite inferior. Por ejemplo, si el límite inferior es 0 y el número de elementos es 10, el límite superior se establecerá automáticamente al 9.  
  
##  <a name="operator_eq"></a>CComSafeArrayBound::operator =  
 Establece el `CComSafeArrayBound` en un nuevo valor.  
  
```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `bound`  
 Objeto `CComSafeArrayBound`.  
  
 `ulCount`  
 Número de elementos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la `CComSafeArrayBound` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El `CComSafeArrayBound` objeto se puede asignar mediante existente `CComSafeArrayBound`, o proporcionando el número de elementos, en el que el límite inferior del caso se establece en 0 de forma predeterminada.  
  
##  <a name="setcount"></a>CComSafeArrayBound::SetCount  
 Llame a este método para establecer el número de elementos.  
  
```
ULONG SetCount(ULONG ulCount) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `ulCount`  
 Número de elementos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de elementos de la `CComSafeArrayBound` objeto.  
  
##  <a name="setlowerbound"></a>CComSafeArrayBound::SetLowerBound  
 Llame a este método para establecer el límite inferior.  
  
```
LONG SetLowerBound(LONG lLowerBound) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `lLowerBound`  
 El límite inferior.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el nuevo límite inferior de la `CComSafeArrayBound` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Si la matriz es tener acceso desde un programa de Visual C++, se recomienda que el límite inferior se define como 0. Es preferible utilizar un valor de límite inferior diferente si la matriz es para su uso con otros lenguajes, como Visual Basic.  
  
 El límite superior depende del número de elementos y el valor de límite inferior. Por ejemplo, si el límite inferior es 0 y el número de elementos es 10, el límite superior se establecerá automáticamente al 9.  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)

