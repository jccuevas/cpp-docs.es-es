---
title: CTypedPtrArray (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTypedPtrArray
- AFXTEMPL/CTypedPtrArray
- AFXTEMPL/CTypedPtrArray::Add
- AFXTEMPL/CTypedPtrArray::Append
- AFXTEMPL/CTypedPtrArray::Copy
- AFXTEMPL/CTypedPtrArray::ElementAt
- AFXTEMPL/CTypedPtrArray::GetAt
- AFXTEMPL/CTypedPtrArray::InsertAt
- AFXTEMPL/CTypedPtrArray::SetAt
- AFXTEMPL/CTypedPtrArray::SetAtGrow
dev_langs:
- C++
helpviewer_keywords:
- pointer arrays
- CTypedPtrArray class
ms.assetid: e3ecdf1a-a889-4156-92dd-ddbd36ccd919
caps.latest.revision: 22
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 24b21d017d46cc88d7e243aff75ccf6383d2c870
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="ctypedptrarray-class"></a>Clase CTypedPtrArray
Proporciona un "contenedor" con seguridad de tipos para objetos de clase `CPtrArray` o `CObArray`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class BASE_CLASS, class TYPE>  
class CTypedPtrArray : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>Parámetros  
 `BASE_CLASS`  
 Clase base de la clase de matriz con tipo de puntero. debe ser una clase de matriz ( `CObArray` o `CPtrArray`).  
  
 `TYPE`  
 Tipo de los elementos almacenados en la matriz de la clase base.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CTypedPtrArray::Add](#add)|Agrega un nuevo elemento al final de una matriz. Crece la matriz si es necesario|  
|[CTypedPtrArray::Append](#append)|Agrega el contenido de una matriz al final de la otra. Crece la matriz si es necesario|  
|[CTypedPtrArray::Copy](#copy)|Copia otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|  
|[CTypedPtrArray::ElementAt](#elementat)|Devuelve una referencia temporal al puntero del elemento dentro de la matriz.|  
|[CTypedPtrArray::GetAt](#getat)|Devuelve el valor en un índice dado.|  
|[CTypedPtrArray::InsertAt](#insertat)|Inserta un elemento (o todos los elementos de otra matriz) en un índice especificado.|  
|[CTypedPtrArray::SetAt](#setat)|Establece el valor de un índice dado; la matriz no puede aumentar de tamaño.|  
|[CTypedPtrArray::SetAtGrow](#setatgrow)|Establece el valor de un índice dado; aumenta el tamaño de la matriz si es necesario.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[[] CTypedPtrArray::operator](#operator_at)|Establece u obtiene el elemento en el índice especificado.|  
  
## <a name="remarks"></a>Comentarios  
 Al usar `CTypedPtrArray` en lugar de `CPtrArray` o `CObArray`, la utilidad de comprobación de tipos de C++ ayuda a eliminar los errores causados por los tipos de puntero no coinciden.  
  
 Además, el `CTypedPtrArray` contenedor realiza gran parte de la conversión que sería necesaria si usó `CObArray` o `CPtrArray`.  
  
 Dado que todos los `CTypedPtrArray` funciones están en línea, el uso de esta plantilla no afecta significativamente el tamaño o la velocidad del código.  
  
 Para obtener más información sobre el uso de `CTypedPtrArray`, consulte los artículos [colecciones](../../mfc/collections.md) y [clases basadas en plantillas](../../mfc/template-based-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `BASE_CLASS`  
  
 `CTypedPtrArray`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtempl.h  
  
##  <a name="add"></a>CTypedPtrArray::Add  
 Llama a esta función miembro `BASE_CLASS` **:: Add**.  
  
```  
INT_PTR Add(TYPE newElement);
```  
  
### <a name="parameters"></a>Parámetros  
 *TIPO DE*  
 Especifica el tipo de elemento que se va a agregar a la matriz de un parámetro de plantilla.  
  
 `newElement`  
 El elemento que se agrega a esta matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del elemento agregado.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener comentarios más detallada, consulte [CObArray::Add](../../mfc/reference/cobarray-class.md#add).  
  
##  <a name="append"></a>CTypedPtrArray::Append  
 Llama a esta función miembro `BASE_CLASS` **:: Append**.  
  
```  
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```  
  
### <a name="parameters"></a>Parámetros  
 `BASE_CLASS`  
 Clase base de la clase de matriz con tipo de puntero. debe ser una clase de matriz ( [CObArray](../../mfc/reference/cobarray-class.md) o [CPtrArray](../../mfc/reference/cptrarray-class.md)).  
  
 *TIPO DE*  
 Tipo de los elementos almacenados en la matriz de la clase base.  
  
 *src*  
 Origen de los elementos que se anexará a una matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del primer elemento anexado.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener comentarios más detallada, consulte [CObArray::Append](../../mfc/reference/cobarray-class.md#append).  
  
##  <a name="copy"></a>CTypedPtrArray::Copy  
 Llama a esta función miembro `BASE_CLASS` **:: copia**.  
  
```  
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```  
  
### <a name="parameters"></a>Parámetros  
 `BASE_CLASS`  
 Clase base de la clase de matriz con tipo de puntero. debe ser una clase de matriz ( [CObArray](../../mfc/reference/cobarray-class.md) o [CPtrArray](../../mfc/reference/cptrarray-class.md)).  
  
 *TIPO DE*  
 Tipo de los elementos almacenados en la matriz de la clase base.  
  
 *src*  
 Origen de los elementos que se copian a una matriz.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener comentarios más detallada, consulte [CObArray::Copy](../../mfc/reference/cobarray-class.md#copy).  
  
##  <a name="elementat"></a>CTypedPtrArray::ElementAt  
 Llama a esta función inline `BASE_CLASS` **:: ElementAt**.  
  
```  
TYPE& ElementAt(INT_PTR nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 *TIPO DE*  
 Parámetro de plantilla que especifica el tipo de elementos almacenados en esta matriz.  
  
 `nIndex`  
 Un índice de entero que es mayor o igual que 0 y menor o igual que el valor devuelto por `BASE_CLASS` **:: GetUpperBound**.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia temporal al elemento en la ubicación especificada por `nIndex`. Este elemento es del tipo especificado por el parámetro de plantilla *tipo*.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener comentarios más detallada, consulte [CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat).  
  
##  <a name="getat"></a>CTypedPtrArray::GetAt  
 Llama a esta función inline `BASE_CLASS` **:: GetAt**.  
  
```  
TYPE GetAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *TIPO DE*  
 Parámetro de plantilla que especifica el tipo de elementos almacenados en la matriz.  
  
 `nIndex`  
 Un índice de entero que es mayor o igual que 0 y menor o igual que el valor devuelto por `BASE_CLASS` **:: GetUpperBound**.  
  
### <a name="return-value"></a>Valor devuelto  
 Una copia del elemento en la ubicación especificada por `nIndex`. Este elemento es del tipo especificado por el parámetro de plantilla *tipo*.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener comentarios más detallada, consulte [CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)  
  
##  <a name="insertat"></a>CTypedPtrArray::InsertAt  
 Llama a esta función miembro `BASE_CLASS` **:: InsertAt**.  
  
```  
void InsertAt(
    INT_PTR nIndex,  
    TYPE newElement,  
    INT_PTR nCount = 1);

 
void InsertAt(
    INT_PTR nStartIndex,  
    CTypedPtrArray<BASE_CLASS, TYPE>* pNewArray);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Un índice de entero que puede ser mayor que el valor devuelto por [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).  
  
 *TIPO DE*  
 Tipo de los elementos almacenados en la matriz de la clase base.  
  
 `newElement`  
 El puntero de objeto que se colocarán en esta matriz. Un `newElement` del valor **NULL** está permitido.  
  
 `nCount`  
 El número de veces que este elemento debe estar insertado (el valor predeterminado es 1).  
  
 `nStartIndex`  
 Un índice de entero que puede ser mayor que el valor devuelto por `CObArray::GetUpperBound`.  
  
 `BASE_CLASS`  
 Clase base de la clase de matriz con tipo de puntero. debe ser una clase de matriz ( [CObArray](../../mfc/reference/cobarray-class.md) o [CPtrArray](../../mfc/reference/cptrarray-class.md)).  
  
 `pNewArray`  
 Otra matriz que contiene los elementos que se agregarán a esta matriz.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener comentarios más detallada, consulte [CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat).  
  
##  <a name="operator_at"></a>[] CTypedPtrArray::operator  
 Llamar estos operadores inline `BASE_CLASS` **:: [] operador**.  
  
```  
TYPE& operator[ ](int_ptr nindex);  
TYPE operator[ ](int_ptr nindex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *TIPO DE*  
 Parámetro de plantilla que especifica el tipo de elementos almacenados en la matriz.  
  
 `nIndex`  
 Un índice de entero que es mayor o igual que 0 y menor o igual que el valor devuelto por `BASE_CLASS` **:: GetUpperBound**.  
  
### <a name="remarks"></a>Comentarios  
 El primer operador denominado para matrices que no sean **const**, puede utilizarse en el (valor r) de la derecha o la izquierda (valor l) de una instrucción de asignación. El segundo, se invoca para **const** matrices, se puede utilizar sólo en la parte derecha.  
  
 La versión de depuración de la biblioteca valida si el subíndice (ya sea en el lado izquierdo o derecho de una instrucción de asignación) está fuera de los límites.  
  
##  <a name="setat"></a>CTypedPtrArray::SetAt  
 Llama a esta función miembro `BASE_CLASS` **:: SetAt**.  
  
```  
void SetAt(
    INT_PTR nIndex,  
    TYPE ptr);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Un índice de entero que es mayor o igual que 0 y menor o igual que el valor devuelto por [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).  
  
 *TIPO DE*  
 Tipo de los elementos almacenados en la matriz de la clase base.  
  
 *PTR*  
 Un puntero al elemento que se va a insertar en la matriz en la nIndex. Se permite un valor NULL.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener comentarios más detallada, consulte [CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat).  
  
##  <a name="setatgrow"></a>CTypedPtrArray::SetAtGrow  
 Llama a esta función miembro `BASE_CLASS` **:: SetAtGrow**.  
  
```  
void SetAtGrow(
    INT_PTR nIndex,  
    TYPE newElement);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de entero que es mayor o igual que 0.  
  
 *TIPO DE*  
 Tipo de los elementos almacenados en la matriz de la clase base.  
  
 `newElement`  
 El puntero de objeto que se agregarán a esta matriz. Un **NULL** se permite el valor.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener comentarios más detallada, consulte [CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC COLLECT](../../visual-cpp-samples.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CPtrArray](../../mfc/reference/cptrarray-class.md)   
 [CObArray (clase)](../../mfc/reference/cobarray-class.md)

