---
title: CTypedPtrMap (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CTypedPtrMap [MFC], GetNextAssoc
- CTypedPtrMap [MFC], Lookup
- CTypedPtrMap [MFC], RemoveKey
- CTypedPtrMap [MFC], SetAt
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cdb0c8679990a48740032017a2c0e11b7148f2d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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
  
|Name|Descripción|  
|----------|-----------------|  
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|Obtiene el elemento siguiente para efectuar una iteración.|  
|[CTypedPtrMap::Lookup](#lookup)|Devuelve un `KEY` tomando como base un `VALUE`.|  
|[CTypedPtrMap::RemoveKey](#removekey)|Quita un elemento especificado por una clave.|  
|[CTypedPtrMap::SetAt](#setat)|Inserta un elemento en la asignación; reemplaza un elemento existente si se encuentra una clave coincidente.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[[] CTypedPtrMap::operator](#operator_at)|Inserta un elemento en el mapa.|  
  
## <a name="remarks"></a>Comentarios  
 Cuando usas `CTypedPtrMap`, la utilidad de comprobación de tipos de C++ ayuda a eliminar errores causados por los tipos de puntero no coinciden.  
  
 Dado que todos los `CTypedPtrMap` funciones están en línea, el uso de esta plantilla no afecta significativamente el tamaño o la velocidad del código.  
  
 Para obtener más información sobre el uso de `CTypedPtrMap`, consulte los artículos [colecciones](../../mfc/collections.md) y [clases basadas en plantillas](../../mfc/template-based-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `BASE_CLASS`  
  
 `CTypedPtrMap`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtempl.h  
  
##  <a name="getnextassoc"></a>  CTypedPtrMap::GetNextAssoc  
 Recupera el elemento de mapa en `rNextPosition`, a continuación, actualiza `rNextPosition` para hacer referencia al elemento siguiente en el mapa.  
  
```  
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `rPosition`  
 Especifica una referencia a un **posición** valor devuelto por un anterior `GetNextAssoc` o `BASE_CLASS` **:: GetHeadPosition** llamar.  
  
 *KEY*  
 Parámetro de plantilla que especifica el tipo de las claves del mapa.  
  
 `rKey`  
 Especifica la clave devuelta del elemento recuperado.  
  
 *VALOR*  
 Parámetro de plantilla que especifica el tipo de valores del mapa.  
  
 `rValue`  
 Especifica el valor devuelto del elemento recuperado.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es muy útil para recorrer en iteración todos los elementos del mapa. Tenga en cuenta que la secuencia de posición no es necesariamente el mismo que la secuencia de valores de clave.  
  
 Si el elemento recuperado es el último en el mapa, a continuación, el nuevo valor de `rNextPosition` está establecido en **NULL**.  
  
 Esta función insertada se llama `BASE_CLASS` **:: GetNextAssoc**.  
  
##  <a name="lookup"></a>  CTypedPtrMap::Lookup  
 `Lookup` aplica un algoritmo hash para encontrar rápidamente el elemento de mapa con una clave que coincide exactamente.  
  
```  
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `BASE_CLASS`  
 Parámetro de plantilla que especifica la clase base de la clase de este mapa.  
  
 `key`  
 La clave del elemento que se va a buscar.  
  
 *VALOR*  
 Especifica el tipo de valores almacenados en este mapa de un parámetro de plantilla.  
  
 `rValue`  
 Especifica el valor devuelto del elemento recuperado.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se encontró el elemento; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función insertada se llama `BASE_CLASS` **:: búsqueda**.  
  
##  <a name="operator_at"></a>  [] CTypedPtrMap::operator  
 Este operador se puede utilizar sólo en el lado izquierdo de una instrucción de asignación (un valor l).  
  
```  
VALUE& operator[ ](base_class ::base_arg_key key);
```  
  
### <a name="parameters"></a>Parámetros  
 *VALOR*  
 Especifica el tipo de valores almacenados en este mapa de un parámetro de plantilla.  
  
 `BASE_CLASS`  
 Parámetro de plantilla que especifica la clase base de la clase de este mapa.  
  
 `key`  
 La clave del elemento que se va a buscar o crear en el mapa.  
  
### <a name="remarks"></a>Comentarios  
 Si no hay ningún elemento de mapa con la clave especificada, se crea un nuevo elemento. No hay ningún "derecha" (valor r) equivalente a este operador porque es posible que no se puede encontrar una clave en el mapa. Use la `Lookup` función de miembro para la recuperación de elemento.  
  
##  <a name="removekey"></a>  CTypedPtrMap::RemoveKey  
 Llama a esta función miembro `BASE_CLASS` **:: RemoveKey**.  
  
```  
BOOL RemoveKey(KEY key);
```  
  
### <a name="parameters"></a>Parámetros  
 *KEY*  
 Parámetro de plantilla que especifica el tipo de las claves del mapa.  
  
 `key`  
 Clave para el elemento va a quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la entrada se encuentra y quita correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener comentarios más detallada, vea [CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey).  
  
##  <a name="setat"></a>  CTypedPtrMap::SetAt  
 Llama a esta función miembro `BASE_CLASS` **:: SetAt**.  
  
```  
void SetAt(KEY key, VALUE newValue);
```  
  
### <a name="parameters"></a>Parámetros  
 *KEY*  
 Parámetro de plantilla que especifica el tipo de las claves del mapa.  
  
 `key`  
 Especifica el valor de clave de la newValue.  
  
 `newValue`  
 Especifica el puntero de objeto que es el valor del nuevo elemento.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener comentarios más detallada, vea [CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC COLLECT](../../visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clase CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)   
 [Clase CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)   
 [Clase CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)   
 [CMapStringToPtr (clase)](../../mfc/reference/cmapstringtoptr-class.md)
