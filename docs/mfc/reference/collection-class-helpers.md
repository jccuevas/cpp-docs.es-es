---
title: Aplicaciones auxiliares de clase de colección | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes [MFC], helper functions
- helper functions collection class [MFC]
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6607f70a18734310d184c5cdd05d1e87f1b82d35
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852361"
---
# <a name="collection-class-helpers"></a>Aplicaciones auxiliares de clase de colección
Las clases de colección `CMap`, `CList`, y `CArray` usar funciones de aplicación auxiliar con plantilla global para estos fines, como comparar, copiar y serializar los elementos. Como parte de la implementación de clases basadas en `CMap`, `CList`, y `CArray`, debe invalidar estas funciones según sea necesario con las versiones adaptadas al tipo de datos almacenados en el mapa, lista o matriz. Para obtener información sobre cómo reemplazar las funciones auxiliares como `SerializeElements`, consulte el artículo [colecciones: realización de una colección segura para el tipo](../../mfc/how-to-make-a-type-safe-collection.md). Tenga en cuenta que `ConstructElements` y `DestructElements` han quedado en desuso.  
  
 La biblioteca Microsoft Foundation Class proporciona las siguientes funciones globales en afxtempl.h que le ayudarán a personalizar sus clases de colección:  
  
### <a name="collection-class-helpers"></a>Aplicaciones auxiliares de clase de colección  
  
|||  
|-|-|  
|[CompareElements](#compareelements)|Indica si los elementos son iguales.|  
|[CopyElements](#copyelements)|Copia los elementos de una matriz a otra.|  
|[DumpElements](#dumpelements)|Proporciona los resultados de diagnóstico orientados a secuencia.|  
|[HashKey](#hashkey)|Calcula una clave hash.|  
|[SerializeElements](#serializeelements)|Almacena o recupera los elementos hacia o desde un archivo.|  
  
##  <a name="compareelements"></a>  CompareElements  
 Llamadas directas [CList::Find] (clist class.md #not_found.md #clist__find e indirectamente por [cmap__lookup](cmap-class.md#lookup) y [cmap__operator &#91; &#93; ](cmap-class.md#operator_at).  
  
```   
template<class TYPE, class ARG_TYPE>  
BOOL AFXAPI  
CompareElements(
    const TYPE* pElement1,  
    const ARG_TYPE* pElement2);  
```  
  
### <a name="parameters"></a>Parámetros  
 *TIPO*  
 El tipo del primer elemento que se va a comparar.  
  
 *pElement1*  
 Puntero al primer elemento que se va a comparar.  
  
 *ARG_TYPE*  
 El tipo del segundo elemento que se va a comparar.  
  
 *pElement2*  
 Puntero al segundo elemento que se va a comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el objeto señalado por *pElement1* es igual que el objeto al que señala *pElement2*; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El `CMap` llama a usar el `CMap` parámetros de plantilla *clave* y *ARG_KEY*.  
  
 La implementación predeterminada devuelve el resultado de la comparación de  *\*pElement1* y  *\*pElement2*. Reemplace esta función para que compare los elementos de una manera que sea adecuada para su aplicación.  
  
 El lenguaje C++ define el operador de comparación ( `==`) para los tipos simples (**char**, **int**, **float**, etc.) pero no define un operador de comparación para las clases y estructuras. Si desea usar `CompareElements` o para crear una instancia de una de las clases de colección que lo utiliza, debe definir el operador de comparación o sobrecarga `CompareElements` con una versión que devuelve los valores adecuados.  
  
### <a name="requirements"></a>Requisitos  
   **Encabezado:** afxtempl.h   
  
##  <a name="copyelements"></a>  CopyElements  
 Esta función se invoca directamente por [CArray::Append](carray-class.md#append) y [CArray::Copy](carray-class.md#copy).  
  
```   
template<class TYPE>  
void AFXAPI CopyElements(
    TYPE* pDest,  
    const TYPE* pSrc,  
    INT_PTR nCount);  
```  
  
### <a name="parameters"></a>Parámetros  
 *TIPO*  
 Parámetro de plantilla que especifica el tipo de elementos que se copiarán.  
  
 *pDest*  
 Puntero a la que se copiarán los elementos de destino.  
  
 *pSrc*  
 Puntero al origen de los elementos que se va a copiar.  
  
 *nCount*  
 Número de elementos que se copiarán.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada usa el operador de asignación simple ( **=** ) para realizar la operación de copia. Si el tipo que se copia no tiene un operador sobrecargado =, la implementación predeterminada realiza una copia bit a bit.  
  
 Para obtener información sobre la implementación de esta y otras funciones auxiliares, consulte el artículo [colecciones: realización de una colección segura para el tipo](../how-to-make-a-type-safe-collection.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxtempl.h  
  
##  <a name="dumpelements"></a>  DumpElements  
 Para los elementos de la colección cuando se invalida, proporciona orientado a secuencias de salida de diagnóstico en forma de texto.  
  
```   
template<class TYPE>  
void  AFXAPI DumpElements(
    CDumpContext& dc,  
    const TYPE* pElements,  
    INT_PTR nCount);  
```  
  
### <a name="parameters"></a>Parámetros  
 *dc*  
 Contexto para volcar los elementos de volcado de memoria.  
  
 *TIPO*  
 Especifica el tipo de los elementos de un parámetro de plantilla.  
  
 *pElements*  
 Puntero a los elementos que se va a volcar.  
  
 *nCount*  
 Número de elementos que se va a volcar.  
  
### <a name="remarks"></a>Comentarios  
 El `CArray::Dump`, `CList::Dump`, y `CMap::Dump` funciones llamar si la profundidad del volcado de memoria es mayor que 0.  
  
 La implementación predeterminada no hace nada. Si se derivan de los elementos de la colección `CObject`, la invalidación normalmente creará una iteración por los elementos de la colección, una llamada a `Dump` para cada elemento a su vez.  
  

### <a name="requirements"></a>Requisitos  
  **Encabezado** afxtempl.h  
  
##  <a name="hashkey"></a>  HashKey  
 Calcula un valor hash para la clave especificada.  
  
```  
template<class ARG_KEY>  
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key); 
```  
  
### <a name="parameters"></a>Parámetros  
 *ARG_KEY*  
 Parámetro de plantilla que especifica el tipo de datos utilizado para tener acceso a las claves del mapa.  
  
 *key*  
 Clave cuyo valor hash se calcula.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de clave hash.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se invoca directamente por [CMap::RemoveKey](cmap-class.md#removekey) e indirectamente por [CMap::Lookup](cmap-class.md#lookup) y [CMap::Operator &#91; &#93; ](cmap-class.md#operator_at).
  
 La implementación predeterminada crea un valor hash trasladando *clave* derecha por cuatro posiciones. Reemplace esta función para que devuelva valores hash adecuada para su aplicación.  
  
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
  
##  <a name="serializeelements"></a>  SerializeElements  
 [CArray](carray-class.md), [CList](clist-class.md), y [CMap](cmap-class.md) llame a esta función para serializar los elementos.  
  
```   
template<class TYPE>  
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);  
```  
  
### <a name="parameters"></a>Parámetros  
 *TIPO*  
 Especifica el tipo de los elementos de un parámetro de plantilla.  
  
 *cuentas por cobrar*  
 Un objeto de almacenamiento para archivar o salientes.  
  
 *pElements*  
 Puntero a los elementos que se archivan.  
  
 *nCount*  
 Número de elementos que se va a archivar  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no bit a bit de lectura o escritura.  
  
 Para obtener información sobre la implementación de esta y otras funciones auxiliares, consulte el artículo [colecciones: realización de una colección segura para el tipo](../how-to-make-a-type-safe-collection.md).  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo en el artículo [colecciones: realización de una colección segura para el tipo](../how-to-make-a-type-safe-collection.md).  
 
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxtempl.h 
    
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [CMap (clase)](cmap-class.md)   
 [CList (clase)](clist-class.md)   
 [CArray (clase)](carray-class.md)