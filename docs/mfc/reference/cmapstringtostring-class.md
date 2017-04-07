---
title: Clase CMapStringToString | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMapStringToString
- AFXCOLL/CMapStringToString
- AFXCOLL/CMapStringToString::CPair
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToString::PGetFirstAssoc
- AFXCOLL/CMapStringToString::PGetNextAssoc
- AFXCOLL/CMapStringToString::PLookup
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
dev_langs:
- C++
helpviewer_keywords:
- collection classes, string mapping
- strings [C++], mapping
- strings [C++], class for mapping
- CMapStringToString class
ms.assetid: b45794c2-fe6b-4edb-a8ca-faa03b57b4a8
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
ms.openlocfilehash: 58ca2023d57c2865dadc8dfab304aab2fa39a96b
ms.lasthandoff: 02/24/2017

---
# <a name="cmapstringtostring-class"></a>Clase CMapStringToString
Admite mapas de objetos `CString` con clave de objetos `CString` .  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMapStringToString : public CObject  
```  
  
## <a name="members"></a>Miembros  
 Las funciones miembro de `CMapStringToString` son similares a las funciones miembro de clase [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Debido a esta similitud, puede utilizar la documentación de referencia de `CMapStringToOb` para obtener información específica de la función miembro. Siempre que vea un `CObject` puntero como parámetro de función de un valor devuelto o "salida" Utilice un puntero a `char`. Siempre que vea un `CObject` puntero como parámetro de función "input", utilice un puntero a `char`.  
  
 `BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`  
  
 por ejemplo, se traduce en  
  
 `BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`  
  
### <a name="public-structures"></a>Estructuras públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMapStringToString::CPair](#cpair)|Una estructura anidada que contiene un valor de clave y el valor del objeto de cadena asociado.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMapStringToOb::CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMapStringToOb::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Devuelve el número de elementos en esta asignación.|  
|[CMapStringToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Determina el número actual de elementos de la tabla hash.|  
|[CMapStringToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Obtiene el siguiente elemento para efectuar una iteración.|  
|[CMapStringToOb::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Devuelve el número de elementos en esta asignación.|  
|[CMapStringToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Devuelve la posición del primer elemento.|  
|[CMapStringToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Calcula el valor hash de una clave especificada.|  
|[CMapStringToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicializa la tabla hash.|  
|[CMapStringToOb::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Pruebas para la condición de asignación vacío (sin elementos).|  
|[CMapStringToOb::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Busca un puntero void basándose en la clave de un puntero void. El valor de puntero, no la entidad que señala, se utiliza para la comparación de claves.|  
|[CMapStringToOb::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Devuelve una referencia a la clave asociada con el valor de clave especificado.|  
|[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)|Obtiene un puntero al primer `CString` en el mapa.|  
|[CMapStringToString::PGetNextAssoc](#pgetnextassoc)|Obtiene un puntero a la siguiente `CString` para efectuar una iteración.|  
|[CMapStringToString::PLookup](#plookup)|Devuelve un puntero a un `CString` cuyo valor coincide con el valor especificado.|  
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Quita todos los elementos de esta asignación.|  
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Quita un elemento especificado mediante una clave.|  
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Inserta un elemento en el mapa; reemplaza un elemento existente si se encuentra una clave coincidente.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[[] CMapStringToOb::operator](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Inserta un elemento en el mapa: sustitución de operador para `SetAt`.|  
  
## <a name="remarks"></a>Comentarios  
 `CMapStringToString` incorpora la macro `IMPLEMENT_SERIAL` para admitir la serialización y el volcado de sus elementos. Cada elemento se serializa a su vez si una asignación se almacena en un archivo, ya sea con la inserción sobrecargada ( ** << **) (operador) o con el `Serialize` función miembro.  
  
 Si se necesita un volcado de individuales `CString` -  `CString` elementos, debe establecer la profundidad del contexto de volcado en 1 o superior.  
  
 Cuando un `CMapStringToString` se elimina el objeto, o cuando se quitan sus elementos, el `CString` los objetos se quitan según corresponda.  
  
 Para obtener más información sobre `CMapStringToString`, vea el artículo [colecciones](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToString`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcoll.h  
  
##  <a name="cpair"></a>CMapStringToString::CPair  
 Contiene un valor de clave y el valor del objeto de cadena asociado.  
  
### <a name="remarks"></a>Comentarios  
 Se trata de una estructura anidada dentro de la clase [CMapStringToString](../../mfc/reference/cmapstringtostring-class.md).  
  
 La estructura se compone de dos campos:  
  
- **clave** el valor real del tipo de clave.  
  
- **valor** el valor del objeto asociado.  
  
 Se utiliza para almacenar los valores devueltos de [CMapStringToString::PLookup](#plookup), [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc), y [CMapStringToString::PGetNextAssoc](#pgetnextassoc).  
  
### <a name="example"></a>Ejemplo  
  Para obtener un ejemplo de uso, vea el ejemplo de [CMapStringToString::PLookup](#plookup).  
  
##  <a name="pgetfirstassoc"></a>CMapStringToString::PGetFirstAssoc  
 Devuelve la primera entrada del objeto map.  
  
```  
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la primera entrada de la asignación; consulte [CMapStringToString::CPair](#cpair). Si el mapa está vacío, el valor es `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para devolver un puntero al primer elemento del objeto map.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections&#73;](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]  
  
##  <a name="pgetnextassoc"></a>CMapStringToString::PGetNextAssoc  
 Recupera el elemento de mapa señalado por `pAssocRec`.  
  
```  
const CPair *PGetNextAssoc(const CPair* pAssoc) const;  
  
CPair *PGetNextAssoc(const CPair* pAssoc);
```  
  
### <a name="parameters"></a>Parámetros  
 *pAssoc*  
 Apunta a una entrada de mapa devuelta por un anterior [PGetNextAssoc](#pgetnextassoc) o [PGetFirstAssoc](#pgetfirstassoc) llamar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la siguiente entrada en la asignación; consulte [CMapStringToString::CPair](#cpair). Si el elemento es el último de la asignación, el valor es **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para recorrer en iteración todos los elementos en el mapa. Recuperar el primer elemento con una llamada a `PGetFirstAssoc` y, a continuación, recorra en iteración el mapa con llamadas sucesivas a `PGetNextAssoc`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc).  
  
##  <a name="plookup"></a>CMapStringToString::PLookup  
 Busca el valor asignado a una clave determinada.  
  
```  
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Puntero a la clave del elemento que se va a buscar.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la clave especificada.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para buscar un elemento de mapa con una clave que coincida exactamente con la clave especificada.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections&#74;](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC COLLECT](../../visual-cpp-samples.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




