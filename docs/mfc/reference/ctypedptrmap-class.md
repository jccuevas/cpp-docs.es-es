---
title: CTypedPtrMap (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTypedPtrMap
- AFXTEMPL/CTypedPtrMap
- AFXTEMPL/CTypedPtrMap::GetNextAssoc
- AFXTEMPL/CTypedPtrMap::Lookup
- AFXTEMPL/CTypedPtrMap::RemoveKey
- AFXTEMPL/CTypedPtrMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- type-safe collections
- template classes, CTypedPtrMap class
- maps
- CTypedPtrMap class
- pointer maps
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
caps.latest.revision: 23
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
ms.openlocfilehash: 919d751c6ffe4b10ffad047f1b6be832bf49a1af
ms.lasthandoff: 02/24/2017

---
# <a name="ctypedptrmap-class"></a>Clase CTypedPtrMap
Proporciona un "contenedor" con seguridad de tipos para objetos de las clases de asignación de puntero `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`y `CMapStringToPtr`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class BASE_CLASS, class KEY, class VALUE>  
class CTypedPtrMap : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>Parámetros  
 `BASE_CLASS`  
 Clase base de la clase de mapa de puntero con tipo. debe ser una clase de mapa de puntero ( `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`, o `CMapStringToPtr`).  
  
 `KEY`  
 Clase del objeto que se utiliza como clave para la asignación.  
  
 `VALUE`  
 Clase del objeto almacenado en el mapa.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|Obtiene el siguiente elemento para efectuar una iteración.|  
|[CTypedPtrMap::Lookup](#lookup)|Devuelve un `KEY` basándose en un `VALUE`.|  
|[CTypedPtrMap::RemoveKey](#removekey)|Quita un elemento especificado mediante una clave.|  
|[CTypedPtrMap::SetAt](#setat)|Inserta un elemento en el mapa; reemplaza un elemento existente si se encuentra una clave coincidente.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[[] CTypedPtrMap::operator](#operator_at)|Inserta un elemento en el mapa.|  
  
## <a name="remarks"></a>Comentarios  
 Al utilizar `CTypedPtrMap`, la utilidad de comprobación de tipos de C++ ayuda a eliminar los errores causados por los tipos de puntero no coinciden.  
  
 Dado que todos los `CTypedPtrMap` funciones están en línea, el uso de esta plantilla no afecta significativamente el tamaño o la velocidad del código.  
  
 Para obtener más información sobre el uso de `CTypedPtrMap`, consulte los artículos [colecciones](../../mfc/collections.md) y [clases basadas en plantillas](../../mfc/template-based-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `BASE_CLASS`  
  
 `CTypedPtrMap`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtempl.h  
  
##  <a name="getnextassoc"></a>CTypedPtrMap::GetNextAssoc  
 Recupera el elemento de mapa en `rNextPosition`, a continuación, actualiza `rNextPosition` para hacer referencia al elemento siguiente en el mapa.  
  
```  
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `rPosition`  
 Especifica una referencia a un **posición** valor devuelto por un método `GetNextAssoc` o `BASE_CLASS` **:: GetHeadPosition** llamar.  
  
 *CLAVE*  
 Parámetro de plantilla que especifica el tipo de las claves del mapa.  
  
 `rKey`  
 Especifica la clave devuelta del elemento recuperado.  
  
 *VALOR*  
 Especifica el tipo de valores de la asignación de un parámetro de plantilla.  
  
 `rValue`  
 Especifica el valor devuelto del elemento recuperado.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es muy útil para recorrer en iteración todos los elementos en el mapa. Tenga en cuenta que la secuencia de posición no es necesariamente el mismo que la secuencia de valores de clave.  
  
 Si el elemento recuperado es el último en el mapa, a continuación, el nuevo valor de `rNextPosition` está establecido en **NULL**.  
  
 Llama a esta función inline `BASE_CLASS` **:: GetNextAssoc**.  
  
##  <a name="lookup"></a>CTypedPtrMap::Lookup  
 `Lookup`utiliza un algoritmo hash para encontrar rápidamente el elemento de mapa con una clave que coincide exactamente.  
  
```  
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `BASE_CLASS`  
 Parámetro de plantilla que especifica la clase base de la clase de este mapa.  
  
 `key`  
 La clave del elemento que se va a buscar.  
  
 *VALOR*  
 Parámetro de plantilla que especifica el tipo de valores almacenados en esta asignación.  
  
 `rValue`  
 Especifica el valor devuelto del elemento recuperado.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se encontró el elemento; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Llama a esta función inline `BASE_CLASS` **:: búsqueda**.  
  
##  <a name="operator_at"></a>[] CTypedPtrMap::operator  
 Este operador se puede utilizar sólo en el lado izquierdo de una instrucción de asignación (un valor l).  
  
```  
VALUE& operator[ ](base_class ::base_arg_key key);
```  
  
### <a name="parameters"></a>Parámetros  
 *VALOR*  
 Parámetro de plantilla que especifica el tipo de valores almacenados en esta asignación.  
  
 `BASE_CLASS`  
 Parámetro de plantilla que especifica la clase base de la clase de este mapa.  
  
 `key`  
 La clave del elemento que se va a buscar o creado en el mapa.  
  
### <a name="remarks"></a>Comentarios  
 Si no hay ningún elemento de mapa con la clave especificada, se crea un nuevo elemento. No hay ningún "derecha" (valor r) equivalente a este operador porque es posible que no se puede encontrar una clave en el mapa. Utilice la `Lookup` función de miembro para la recuperación de elemento.  
  
##  <a name="removekey"></a>CTypedPtrMap::RemoveKey  
 Llama a esta función miembro `BASE_CLASS` **:: RemoveKey**.  
  
```  
BOOL RemoveKey(KEY key);
```  
  
### <a name="parameters"></a>Parámetros  
 *CLAVE*  
 Parámetro de plantilla que especifica el tipo de las claves del mapa.  
  
 `key`  
 Clave del elemento que se quita.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la entrada se encuentra y quita correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener comentarios más detallada, consulte [CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey).  
  
##  <a name="setat"></a>CTypedPtrMap::SetAt  
 Llama a esta función miembro `BASE_CLASS` **:: SetAt**.  
  
```  
void SetAt(KEY key, VALUE newValue);
```  
  
### <a name="parameters"></a>Parámetros  
 *CLAVE*  
 Parámetro de plantilla que especifica el tipo de las claves del mapa.  
  
 `key`  
 Especifica el valor de clave de la newValue.  
  
 `newValue`  
 Especifica el puntero de objeto que es el valor del nuevo elemento.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener comentarios más detallada, consulte [CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC COLLECT](../../visual-cpp-samples.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)   
 [Clase CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)   
 [Clase CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)   
 [Clase CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)

