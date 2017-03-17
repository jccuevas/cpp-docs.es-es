---
title: Clase CMap | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMap
- AFXTEMPL/CMap
- AFXTEMPL/CMap::CPair
- AFXTEMPL/CMap::CMap
- AFXTEMPL/CMap::GetCount
- AFXTEMPL/CMap::GetHashTableSize
- AFXTEMPL/CMap::GetNextAssoc
- AFXTEMPL/CMap::GetSize
- AFXTEMPL/CMap::GetStartPosition
- AFXTEMPL/CMap::InitHashTable
- AFXTEMPL/CMap::IsEmpty
- AFXTEMPL/CMap::Lookup
- AFXTEMPL/CMap::PGetFirstAssoc
- AFXTEMPL/CMap::PGetNextAssoc
- AFXTEMPL/CMap::PLookup
- AFXTEMPL/CMap::RemoveAll
- AFXTEMPL/CMap::RemoveKey
- AFXTEMPL/CMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- dictionary mapping class
- collection classes, dictionary mapping
- CMap class
ms.assetid: 640a45ab-0993-4def-97ec-42cc78eb10b9
caps.latest.revision: 24
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
ms.openlocfilehash: 680d44fe6154861d2c638697cfc9d3fbeab36cc4
ms.lasthandoff: 02/24/2017

---
# <a name="cmap-class"></a>Clase CMap
Una clase de colección de diccionarios que asigna claves únicas a valores.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject  
```  
  
#### <a name="parameters"></a>Parámetros  
 `KEY`  
 Clase del objeto que se utiliza como clave para la asignación.  
  
 `ARG` *_* `KEY`  
 Tipo de datos utilizado para `KEY` argumentos; normalmente una referencia a `KEY`.  
  
 `VALUE`  
 Clase del objeto almacenado en el mapa.  
  
 `ARG` *_* `VALUE`  
 Tipo de datos utilizado para `VALUE` argumentos; normalmente una referencia a `VALUE`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-structures"></a>Estructuras públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMap::CPair](#cpair)|Una estructura anidada que contiene un valor de clave y el valor del objeto asociado.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMap::CMap](#cmap)|Crea una colección que asigna claves a valores.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMap::GetCount](#getcount)|Devuelve el número de elementos en esta asignación.|  
|[CMap::GetHashTableSize](#gethashtablesize)|Devuelve el número de elementos en la tabla hash.|  
|[CMap::GetNextAssoc](#getnextassoc)|Obtiene el siguiente elemento para efectuar una iteración.|  
|[CMap::GetSize](#getsize)|Devuelve el número de elementos en esta asignación.|  
|[CMap::GetStartPosition](#getstartposition)|Devuelve la posición del primer elemento.|  
|[CMap::InitHashTable](#inithashtable)|Inicializa la tabla hash y especifica su tamaño.|  
|[CMap::IsEmpty](#isempty)|Pruebas para la condición de asignación vacío (sin elementos).|  
|[CMap::Lookup](#lookup)|Busca el valor asignado a una clave determinada.|  
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|Devuelve un puntero al primer elemento.|  
|[CMap::PGetNextAssoc](#pgetnextassoc)|Obtiene un puntero al siguiente elemento para efectuar una iteración.|  
|[CMap::PLookup](#plookup)|Devuelve un puntero a una clave cuyo valor coincide con el valor especificado.|  
|[CMap::RemoveAll](#removeall)|Quita todos los elementos de esta asignación.|  
|[CMap::RemoveKey](#removekey)|Quita un elemento especificado mediante una clave.|  
|[CMap::SetAt](#setat)|Inserta un elemento en el mapa; reemplaza un elemento existente si se encuentra una clave coincidente.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[[] CMap::operator](#operator_at)|Inserta un elemento en la utilización del mapa â €"sustitución de operador para `SetAt`.|  
  
## <a name="remarks"></a>Comentarios  
 Una vez que haya insertado un par de clave y valor (elemento) en el mapa, puede recuperar eficazmente o eliminar el par mediante la clave para tener acceso a él. También puede iterar por todos los elementos en el mapa.  
  
 Una variable de tipo **posición** se usa para el acceso alternativo a las entradas. Puede usar un **posición** "recordar" una entrada y para recorrer en iteración el mapa. Podría pensar que esta iteración es secuencial por valor de clave; no es así. La secuencia de elementos recuperados es indeterminada.  
  
 Determinadas funciones miembro de esta llamada de clase de funciones auxiliares globales que deben personalizarse para la mayoría de los usos de la `CMap` clase. Consulte [aplicaciones auxiliares de clase de colección](../../mfc/reference/collection-class-helpers.md) en la sección de Macros y funciones globales de la `MFC``Reference`.  
  
 `CMap`reemplaza [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) para admitir la serialización y el volcado de sus elementos. Si una asignación se almacena en un archivo con `Serialize`, cada elemento de mapa se serializa a su vez. La implementación predeterminada de la `SerializeElements` función auxiliar realiza una escritura bit a bit. Para obtener información sobre la serialización de los elementos de la colección de puntero derivados `CObject` o de otros tipos definidos por el usuario, consulte [Cómo: crear una colección con seguridad de tipos](../../mfc/how-to-make-a-type-safe-collection.md).  
  
 Si necesita un volcado de diagnóstico de los elementos individuales de la asignación (las claves y valores), debe establecer la profundidad del contexto de volcado en 1 o superior.  
  
 Cuando un `CMap` se elimina el objeto, o cuando se quitan sus elementos, se quitan las claves y valores.  
  
 Derivación de la clase Map es similar a la derivación de la lista. Consulte el artículo [colecciones](../../mfc/collections.md) para ver una ilustración de la derivación de una clase de lista de propósito especial.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMap`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtempl.h  
  
##  <a name="cmap"></a>CMap::CMap  
 Construye un mapa vacío.  
  
```  
CMap(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>Parámetros  
 `nBlockSize`  
 Especifica la granularidad de asignación de memoria para ampliar el mapa.  
  
### <a name="remarks"></a>Comentarios  
 A medida que crece la asignación, se asigna memoria en unidades de `nBlockSize` entradas.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections nº&56;](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]  
  
##  <a name="cpair"></a>CMap::CPair  
 Contiene un valor de clave y el valor del objeto asociado.  
  
### <a name="remarks"></a>Comentarios  
 Se trata de una estructura anidada dentro de la clase [CMap](../../mfc/reference/cmap-class.md).  
  
 La estructura se compone de dos campos:  
  
- **keyÂ Â Â** el valor real del tipo de clave.  
  
- **valueÂ Â Â** el valor del objeto asociado.  
  
 Se utiliza para almacenar los valores devueltos de [CMap::PLookup](#plookup), [CMap::PGetFirstAssoc](#pgetfirstassoc), y [CMap::PGetNextAssoc](#pgetnextassoc).  
  
### <a name="example"></a>Ejemplo  
 Para obtener un ejemplo de uso, vea el ejemplo de [CMap::PLookup](#plookup).  
  
##  <a name="getcount"></a>CMap::GetCount  
 Recupera el número de elementos en el mapa.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de elementos.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMap::Lookup](#lookup).  
  
##  <a name="gethashtablesize"></a>CMap::GetHashTableSize  
 Determina el número de elementos de la tabla hash para la asignación.  
  
```  
UINT GetHashTableSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos de la tabla hash.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections&#57;](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]  
  
##  <a name="getnextassoc"></a>CMap::GetNextAssoc  
 Recupera el elemento de mapa en `rNextPosition`, a continuación, actualiza `rNextPosition` para hacer referencia al elemento siguiente en el mapa.  
  
```  
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `rNextPosition`  
 Especifica una referencia a un **posición** valor devuelto por un método `GetNextAssoc` o `GetStartPosition` llamar.  
  
 *CLAVE*  
 Parámetro de plantilla que especifica el tipo de clave del mapa.  
  
 `rKey`  
 Especifica la clave devuelta del elemento recuperado.  
  
 *VALOR*  
 Especifica el tipo del valor de la asignación de un parámetro de plantilla.  
  
 `rValue`  
 Especifica el valor devuelto del elemento recuperado.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es muy útil para recorrer en iteración todos los elementos en el mapa. Tenga en cuenta que la secuencia de posición no es necesariamente el mismo que la secuencia de valores de clave.  
  
 Si el elemento recuperado es el último en el mapa, a continuación, el nuevo valor de `rNextPosition` está establecido en **NULL**.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMap::SetAt](#setat).  
  
##  <a name="getsize"></a>CMap::GetSize  
 Devuelve el número de elementos de mapa.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos en el mapa.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para recuperar el número de elementos en el mapa.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections&#58;](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="getstartposition"></a>CMap::GetStartPosition  
 Inicia una iteración de mapa devolviendo un **posición** valor que se puede pasar a un `GetNextAssoc` llamar.  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un **posición** valor que indica la posición de comienzo para recorrer en iteración el mapa; o **NULL** si el mapa está vacío.  
  
### <a name="remarks"></a>Comentarios  
 La secuencia de la iteración no es de predicción; por lo tanto, el "primer elemento en el mapa" no tiene especial importancia.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMap::SetAt](#setat).  
  
##  <a name="inithashtable"></a>CMap::InitHashTable  
 Inicializa la tabla hash.  
  
```  
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUEÂ);  
```  
  
### <a name="parameters"></a>Parámetros  
 `hashSize`  
 Número de entradas en la tabla hash.  
  
 `bAllocNow`  
 Si **TRUE**, asigna la tabla hash en la inicialización; de lo contrario, la tabla se asigna cuando sea necesario.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener un rendimiento óptimo, el tamaño de la tabla hash debe ser un número primo. Para minimizar los conflictos, el tamaño debe ser aproximadamente 20 por ciento mayor que el mayor conjunto de datos previsto.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMap::Lookup](#lookup).  
  
##  <a name="isempty"></a>CMap::IsEmpty  
 Determina si el mapa está vacío.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si esta asignación no contiene elementos; en caso contrario, 0.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMap::RemoveAll](#removeall).  
  
##  <a name="lookup"></a>CMap::Lookup  
 Busca el valor asignado a una clave determinada.  
  
```  
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `ARG_KEY`  
 Parámetro de plantilla que especifica el tipo de la `key` valor.  
  
 `key`  
 Especifica la clave que identifica el elemento que se va a buscar.  
  
 *VALOR*  
 Especifica el tipo del valor que se va a buscar.  
  
 `rValue`  
 Recibe el valor buscado.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se encontró el elemento; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 `Lookup`utiliza un algoritmo hash para encontrar rápidamente el elemento de mapa con una clave que coincida exactamente con la clave especificada.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections&#58;](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="operator_at"></a>[] CMap::operator  
 Un sustituto adecuado para la `SetAt` función miembro.  
  
```  
VALUE& operator[](arg_key key);
```  
  
### <a name="parameters"></a>Parámetros  
 *VALOR*  
 Especifica el tipo del valor de asignación de un parámetro de plantilla.  
  
 `ARG_KEY`  
 Parámetro de plantilla que especifica el tipo del valor de clave.  
  
 `key`  
 La clave utilizada para recuperar el valor de la asignación.  
  
### <a name="remarks"></a>Comentarios  
 Por lo tanto puede utilizarse sólo en el lado izquierdo de una instrucción de asignación (un valor l). Si no hay ningún elemento de mapa con la clave especificada, se crea un nuevo elemento.  
  
 No hay ningún "derecha" (valor r) equivalente a este operador porque es posible que no se puede encontrar una clave en el mapa. Utilice la `Lookup` función de miembro para la recuperación de elemento.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMap::Lookup](#lookup).  
  
##  <a name="pgetfirstassoc"></a>CMap::PGetFirstAssoc  
 Devuelve la primera entrada del objeto map.  
  
```  
const CPair* PGetFirstAssoc() const;Â CPair* PGetFirstAssoc();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la primera entrada de la asignación; consulte [CMap::CPair](#cpair). Si la asignación no contiene ninguna entrada, el valor es **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para devolver un puntero al primer elemento del objeto map.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections&#59;](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]  
  
##  <a name="pgetnextassoc"></a>CMap::PGetNextAssoc  
 Recupera el elemento de mapa señalado por `pAssocRec`.  
  
```  
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;  
  
CPair *PGetNextAssoc(const CPair* pAssocRet);
```  
  
### <a name="parameters"></a>Parámetros  
 *pAssocRet*  
 Apunta a una entrada de mapa devuelta por un anterior [PGetNextAssoc](#pgetnextassoc) o [CMap::PGetFirstAssoc](#pgetfirstassoc) llamar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la siguiente entrada en la asignación; consulte [CMap::CPair](#cpair). Si el elemento es el último de la asignación, el valor es **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para recorrer en iteración todos los elementos en el mapa. Recuperar el primer elemento con una llamada a `PGetFirstAssoc` y, a continuación, recorra en iteración el mapa con llamadas sucesivas a `PGetNextAssoc`.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMap::PGetFirstAssoc](#pgetfirstassoc).  
  
##  <a name="plookup"></a>CMap::PLookup  
 Busca el valor asignado a una clave determinada.  
  
```  
const CPair* PLookup(ARG_KEY  key) const;
CPair* PLookup(Â    ARG_KEY  keyÂ);  ```  
  
### Parameters  
 `key`  
 Key for the element to be searched for.  
  
### Return Value  
 A pointer to a key structure; see [CMap::CPair](#cpair). If no match is found, `CMap::PLookup` returns `NULL`.  
  
### Remarks  
 Call this method to search for a map element with a key that exactly matches the given key.  
  
### Example  
 [!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]  
  
##  <a name="removeall"></a>  CMap::RemoveAll  
 Removes all the values from this map by calling the global helper function **DestructElements**.  
  
```  
void RemoveAll();
```  
  
### Remarks  
 The function works correctly if the map is already empty.  
  
### Example  
 [!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]  
  
##  <a name="removekey"></a>  CMap::RemoveKey  
 Looks up the map entry corresponding to the supplied key; then, if the key is found, removes the entry.  
  
```  
BOOL RemoveKey(ARG_KEY key);
```  
  
### Parameters  
 `ARG_KEY`  
 Template parameter specifying the type of the key.  
  
 `key`  
 Key for the element to be removed.  
  
### Return Value  
 Nonzero if the entry was found and successfully removed; otherwise 0.  
  
### Remarks  
 The **DestructElements** helper function is used to remove the entry.  
  
### Example  
 See the example for [CMap::SetAt](#setat).  
  
##  <a name="setat"></a>  CMap::SetAt  
 The primary means to insert an element in a map.  
  
```  
void SetAt (ARG_KEY de newValue ARG_VALUE clave,)
```  
  
### Parameters  
 `ARG_KEY`  
 Template parameter specifying the type of the `key` parameter.  
  
 `key`  
 Specifies the key of the new element.  
  
 `ARG_VALUE`  
 Template parameter specifying the type of the `newValue` parameter.  
  
 `newValue`  
 Specifies the value of the new element.  
  
### Remarks  
 First, the key is looked up. If the key is found, then the corresponding value is changed; otherwise a new key-value pair is created.  
  
### Example  
 [!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]  
  
## See Also  
 [MFC Sample COLLECT](../../visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)  

