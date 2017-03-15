---
title: "Aplicaciones auxiliares de clase de colección | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes, helper functions
- helper functions collection class
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
caps.latest.revision: 14
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: d2649ef9c8b0320a94ec28a2341baa0f768b07d0
ms.lasthandoff: 02/24/2017

---
# <a name="collection-class-helpers"></a>Aplicaciones auxiliares de clase de colección
Las clases de colección `CMap`, `CList`, y `CArray` usar funciones de aplicación auxiliar con plantilla global para estos fines, como comparar, copiar y seleccionar elementos. Como parte de la implementación de clases basadas en `CMap`, `CList`, y `CArray`, debe invalidar estas funciones según sea necesario con las versiones adaptadas para el tipo de datos almacenados en el mapa, lista o matriz. Para obtener información sobre cómo reemplazar las funciones auxiliares como `SerializeElements`, vea el artículo [colecciones: cómo crear una colección con seguridad de tipos](../../mfc/how-to-make-a-type-safe-collection.md). Tenga en cuenta que **ConstructElements** y **DestructElements** han quedado en desuso.  
  
 La biblioteca Microsoft Foundation Class proporciona las siguientes funciones globales en afxtempl.h que le ayudarán a personalizar sus clases de colección:  
  
### <a name="collection-class-helpers"></a>Aplicaciones auxiliares de clase de colección  
  
|||  
|-|-|  
|[CompareElements](#compareelements)|Indica si los elementos son iguales.|  
|[CopyElements](#copyelements)|Copia los elementos de una matriz a otra.|  
|[DumpElements](#dumpelements)|Proporciona los resultados de diagnóstico orientados a secuencias.|  
|[HashKey](#hashkey)|Calcula una clave hash.|  
|[SerializeElements](#serializeelements)|Almacena o recupera elementos a o desde un archivo.|  
  
##  <a name="a-namecompareelementsa--compareelements"></a><a name="compareelements"></a>CompareElements  
 Llamadas directas [CList::Find] (clist class.md #not_found.md #clist__find e indirectamente [cmap__lookup](cmap-class.md#lookup) y [[] cmap__operator](cmap-class.md#operator_at).  
  
```   
template<class TYPE, class ARG_TYPE>  
BOOL AFXAPI  
CompareElements(
    const TYPE* pElement1,  
    const ARG_TYPE* pElement2);  
```  
  
### <a name="parameters"></a>Parámetros  
 *TIPO DE*  
 El tipo del primer elemento que se va a comparar.  
  
 `pElement1`  
 Puntero al primer elemento que se va a comparar.  
  
 `ARG_TYPE`  
 El tipo del segundo elemento se va a comparar.  
  
 `pElement2`  
 Puntero al segundo elemento se va a comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el objeto al que apunta `pElement1` es igual que el objeto al que señala `pElement2`; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El `CMap` llama uso el `CMap` parámetros de plantilla *clave* y `ARG_KEY`.  
  
 La implementación predeterminada devuelve el resultado de la comparación de * \*pElement1* y * \*pElement2*. Reemplazar esta función para que compara los elementos de una manera que sea adecuada para su aplicación.  
  
 El lenguaje C++ define el operador de comparación ( `==`) para los tipos simples ( `char`, `int`, **float**, etc.) pero no define un operador de comparación para las clases y estructuras. Si desea usar `CompareElements` o para crear una instancia de una de las clases de colección que lo utiliza, debe definir el operador de comparación o sobrecarga `CompareElements` con una versión que devuelve los valores adecuados.  
  
### <a name="requirements"></a>Requisitos  
   **Encabezado:** afxtempl.h   
  
##  <a name="a-namecopyelementsa--copyelements"></a><a name="copyelements"></a>CopyElements  
 Esta función se invoca directamente a [CArray::Append](carray-class.md#append) y [CArray::Copy](carray-class.md#copy).  
  
```   
template<class TYPE>  
void AFXAPI CopyElements(
    TYPE* pDest,  
    const TYPE* pSrc,  
    INT_PTR nCount);  
```  
  
### <a name="parameters"></a>Parámetros  
 *TIPO DE*  
 Parámetro de plantilla que especifica el tipo de elementos que se copian.  
  
 `pDest`  
 Puntero al destino donde se copiarán los elementos.  
  
 `pSrc`  
 Puntero al origen de los elementos que se va a copiar.  
  
 `nCount`  
 Número de elementos copiados.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada usa el operador de asignación simple ( ** = ** ) para realizar la operación de copia. Si el tipo que se está copiando no tiene un operador sobrecargado =, la implementación predeterminada realiza una copia bit a bit.  
  
 Para obtener información sobre la implementación de esta y otras funciones auxiliares, vea el artículo [colecciones: cómo crear una colección con seguridad de tipos](../how-to-make-a-type-safe-collection.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxtempl.h  
  
##  <a name="a-namedumpelementsa--dumpelements"></a><a name="dumpelements"></a>DumpElements  
 Proporciona los resultados de diagnóstico orientados a secuencia en forma de texto para los elementos de la colección cuando se reemplaza.  
  
```   
template<class TYPE>  
void  AFXAPI DumpElements(
    CDumpContext& dc,  
    const TYPE* pElements,  
    INT_PTR nCount);  
```  
  
### <a name="parameters"></a>Parámetros  
 `dc`  
 Volcar contexto para volcar los elementos.  
  
 *TIPO DE*  
 Especifica el tipo de los elementos de un parámetro de plantilla.  
  
 `pElements`  
 Puntero a los elementos que se va a volcar.  
  
 `nCount`  
 Número de elementos que se va a volcar.  
  
### <a name="remarks"></a>Comentarios  
 El **CArray::Dump**, **CList::Dump**, y **CMap::Dump** funciones llamar si la profundidad del volcado de memoria es mayor que 0.  
  
 La implementación predeterminada no hace nada. Si se derivan de los elementos de la colección de `CObject`, la invalidación normalmente recorrer los elementos de la colección, una llamada a `Dump` para cada elemento de turno.  
  

### <a name="requirements"></a>Requisitos  
  **Encabezado** afxtempl.h  
  
##  <a name="a-namehashkeya--hashkey"></a><a name="hashkey"></a>HashKey  
 Calcula un valor hash con la clave dada.  
  
```  
template<class ARG_KEY>  
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key); 
```  
  
### <a name="parameters"></a>Parámetros  
 `ARG_KEY`  
 Parámetro de plantilla que especifica el tipo de datos utilizado para tener acceso a claves de asignación.  
  
 `key`  
 Clave cuyo valor hash se va a calcular.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor hash de la clave.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se invoca directamente a [CMap::RemoveKey](cmap-class.md#removekey) e indirectamente [CMap::Lookup](cmap-class.md#lookup) y [[] CMap::Operator](cmap-class.md#operator_at).
  
 La implementación predeterminada crea un valor hash desplazando `key` derecha por cuatro posiciones. Reemplazar esta función para que devuelva valores hash adecuada para su aplicación.  
  
### <a name="example"></a>Ejemplo
 ```cpp  
template <> UINT AFXAPI HashKey(unsigned __int64 key)
{
   // Generate the hash value by XORing the lower 32 bits of the number 
   // with the upper 32 bits
   return(UINT(key) ^ UINT(key >> 32));
}
 ```
 
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxtempl.h 
  
##  <a name="a-nameserializeelementsa--serializeelements"></a><a name="serializeelements"></a>SerializeElements  
 [CArray](carray-class.md), [CList](clist-class.md), y [CMap](cmap-class.md) llame a esta función para serializar elementos.  
  
```   
template<class TYPE>  
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);  
```  
  
### <a name="parameters"></a>Parámetros  
 *TIPO DE*  
 Especifica el tipo de los elementos de un parámetro de plantilla.  
  
 `ar`  
 Archivar a o desde un objeto de almacenamiento.  
  
 `pElements`  
 Puntero a los elementos que se archivan.  
  
 `nCount`  
 Número de elementos que se estén almacenando  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada realiza un bit a bit de lectura o escritura.  
  
 Para obtener información sobre la implementación de esta y otras funciones auxiliares, vea el artículo [colecciones: cómo crear una colección con seguridad de tipos](../how-to-make-a-type-safe-collection.md).  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo en el artículo [colecciones: cómo crear una colección con seguridad de tipos](../how-to-make-a-type-safe-collection.md).  
 
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxtempl.h 
    
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [Clase CMap](cmap-class.md)   
 [CList (clase)](clist-class.md)   
 [CArray (clase)](carray-class.md)
