---
title: Clase CMap | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
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
- CMap [MFC], CPair
- CMap [MFC], CMap
- CMap [MFC], GetCount
- CMap [MFC], GetHashTableSize
- CMap [MFC], GetNextAssoc
- CMap [MFC], GetSize
- CMap [MFC], GetStartPosition
- CMap [MFC], InitHashTable
- CMap [MFC], IsEmpty
- CMap [MFC], Lookup
- CMap [MFC], PGetFirstAssoc
- CMap [MFC], PGetNextAssoc
- CMap [MFC], PLookup
- CMap [MFC], RemoveAll
- CMap [MFC], RemoveKey
- CMap [MFC], SetAt
ms.assetid: 640a45ab-0993-4def-97ec-42cc78eb10b9
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bd7c1b23e3c586bf89a86e17d85ee5b5050fbf37
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
  
|nombre|Descripción|  
|----------|-----------------|  
|[CMap::CPair](#cpair)|Una estructura anidada que contiene un valor de clave y el valor del objeto asociado.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMap::CMap](#cmap)|Construye una colección que asigna claves a valores.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMap::GetCount](#getcount)|Devuelve el número de elementos de esta asignación.|  
|[CMap::GetHashTableSize](#gethashtablesize)|Devuelve el número de elementos en la tabla hash.|  
|[CMap::GetNextAssoc](#getnextassoc)|Obtiene el elemento siguiente para efectuar una iteración.|  
|[CMap::GetSize](#getsize)|Devuelve el número de elementos de esta asignación.|  
|[CMap::GetStartPosition](#getstartposition)|Devuelve la posición del primer elemento.|  
|[CMap::InitHashTable](#inithashtable)|Inicializa la tabla hash y especifica su tamaño.|  
|[CMap::IsEmpty](#isempty)|Comprueba si la condición de mapa está vacío (no hay elementos).|  
|[CMap::Lookup](#lookup)|Busca el valor asignado a una clave determinada.|  
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|Devuelve un puntero al primer elemento.|  
|[CMap::PGetNextAssoc](#pgetnextassoc)|Obtiene un puntero al elemento siguiente para efectuar una iteración.|  
|[CMap::PLookup](#plookup)|Devuelve un puntero a una clave cuyo valor coincide con el valor especificado.|  
|[CMap::RemoveAll](#removeall)|Quita todos los elementos de esta asignación.|  
|[CMap::RemoveKey](#removekey)|Quita un elemento especificado por una clave.|  
|[CMap::SetAt](#setat)|Inserta un elemento en la asignación; reemplaza un elemento existente si se encuentra una clave coincidente.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[[] CMap::operator](#operator_at)|Inserta un elemento en el mapa: sustitución de operador para `SetAt`.|  
  
## <a name="remarks"></a>Comentarios  
 Una vez que ha insertado un par de clave y valor (elemento) en el mapa, puede recuperar eficazmente o eliminar el par con la clave para tener acceso a él. También puede iterar por todos los elementos del mapa.  
  
 Una variable de tipo **posición** se usa para el acceso alternativo a las entradas. Puede usar un **posición** "recordar" una entrada y para recorrer en iteración el mapa. Puede que piense que esta iteración es secuencial por valor de clave; no es así. La secuencia de elementos recuperados es indeterminada.  
  
 Algunas funciones de miembro de esta llamada de clase auxiliar global, las funciones que deben personalizarse para la mayoría de los usos de la `CMap` clase. Vea [aplicaciones auxiliares de clase de colección](../../mfc/reference/collection-class-helpers.md) en la sección de Macros y funciones globales de la `MFC Reference`.  
  
 `CMap`invalida [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) para admitir la serialización y el volcado de sus elementos. Si una asignación se almacena en un archivo con `Serialize`, cada elemento de mapa se serializa a su vez. La implementación predeterminada de la `SerializeElements` función auxiliar realiza una escritura bit a bit. Para obtener información acerca de la serialización de los elementos de la colección de puntero derivado de `CObject` o de otros tipos definidos por el usuario, consulte [Cómo: crear una colección con seguridad de tipos](../../mfc/how-to-make-a-type-safe-collection.md).  
  
 Si necesita un volcado de diagnóstico de los elementos individuales de la asignación (los valores y claves), debe establecer la profundidad del contexto de volcado en 1 o mayor.  
  
 Cuando un `CMap` se elimina el objeto, o cuando se quitan sus elementos, se quitan las claves y valores.  
  
 Derivación de la clase Map es similar a la derivación de la lista. Vea el artículo [colecciones](../../mfc/collections.md) para ver una ilustración de la derivación de una clase de lista de propósito especial.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMap`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtempl.h  
  
##  <a name="cmap"></a>CMap::CMap  
 Crea una asignación vacía.  
  
```  
CMap(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>Parámetros  
 `nBlockSize`  
 Especifica la granularidad de asignación de memoria para extender la asignación.  
  
### <a name="remarks"></a>Comentarios  
 A medida que aumenta la asignación, se asigna memoria en unidades de `nBlockSize` entradas.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]  
  
##  <a name="cpair"></a>CMap::CPair  
 Contiene un valor de clave y el valor del objeto asociado.  
  
### <a name="remarks"></a>Comentarios  
 Se trata de una estructura anidada dentro de la clase [CMap](../../mfc/reference/cmap-class.md).  
  
 La estructura se compone de dos campos:  
  
- **clave** el valor real del tipo de clave.  
  
- **valor** el valor del objeto asociado.  
  
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
 [!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]  
  
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
 Especifica una referencia a un **posición** valor devuelto por un anterior `GetNextAssoc` o `GetStartPosition` llamar.  
  
 *KEY*  
 Parámetro de plantilla que especifica el tipo de clave del mapa.  
  
 `rKey`  
 Especifica la clave devuelta del elemento recuperado.  
  
 *VALOR*  
 Especifica el tipo del valor de la asignación de un parámetro de plantilla.  
  
 `rValue`  
 Especifica el valor devuelto del elemento recuperado.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es muy útil para recorrer en iteración todos los elementos del mapa. Tenga en cuenta que la secuencia de posición no es necesariamente el mismo que la secuencia de valores de clave.  
  
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
 Llamar a este método para recuperar el número de elementos en el mapa.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="getstartposition"></a>CMap::GetStartPosition  
 Inicie una iteración de mapa devolviendo un **posición** valor que se puede pasar a un `GetNextAssoc` llamar a.  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 A **posición** valor que indica una posición inicial para efectuar una iteración del objeto map; o **NULL** si el mapa está vacío.  
  
### <a name="remarks"></a>Comentarios  
 La secuencia de la iteración no es de predicción; por lo tanto, el "primer elemento en el mapa" no tiene ninguna importancia especial.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMap::SetAt](#setat).  
  
##  <a name="inithashtable"></a>CMap::InitHashTable  
 Inicializa la tabla hash.  
  
```  
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);  
```  
  
### <a name="parameters"></a>Parámetros  
 `hashSize`  
 Número de entradas en la tabla hash.  
  
 `bAllocNow`  
 Si **TRUE**, asigna la tabla hash en la inicialización; en caso contrario, se asigna a la tabla cuando sea necesario.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener el mejor rendimiento, el tamaño de la tabla hash debe ser un número primo. Para minimizar los conflictos, el tamaño debe ser aproximadamente 20 por ciento mayor que el conjunto de datos previsto más grande.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMap::Lookup](#lookup).  
  
##  <a name="isempty"></a>CMap::IsEmpty  
 Determina si el mapa está vacío.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si esta asignación no contiene elementos; en caso contrario es 0.  
  
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
 Es distinto de cero si se encontró el elemento; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 `Lookup`aplica un algoritmo hash para encontrar rápidamente el elemento de mapa con una clave que coincida exactamente con la clave dada.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="operator_at"></a>[] CMap::operator  
 Un sustituto adecuado para la `SetAt` función miembro.  
  
```  
VALUE& operator[](arg_key key);
```  
  
### <a name="parameters"></a>Parámetros  
 *VALOR*  
 Parámetro de plantilla que especifica el tipo del valor de mapa.  
  
 `ARG_KEY`  
 Parámetro de plantilla que especifica el tipo del valor de clave.  
  
 `key`  
 La clave utilizada para recuperar el valor de la asignación.  
  
### <a name="remarks"></a>Comentarios  
 Lo que se puede utilizar sólo en el lado izquierdo de una instrucción de asignación (un valor l). Si no hay ningún elemento de mapa con la clave especificada, se crea un nuevo elemento.  
  
 No hay ningún "derecha" (valor r) equivalente a este operador porque es posible que no se puede encontrar una clave en el mapa. Use la `Lookup` función de miembro para la recuperación de elemento.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMap::Lookup](#lookup).  
  
##  <a name="pgetfirstassoc"></a>CMap::PGetFirstAssoc  
 Devuelve la primera entrada del objeto map.  
  
```  
const CPair* PGetFirstAssoc() const; 
CPair* PGetFirstAssoc();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la primera entrada en la asignación; vea [CMap::CPair](#cpair). Si la asignación no contiene ninguna entrada, el valor es **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para devolver un puntero al primer elemento del objeto map.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]  
  
##  <a name="pgetnextassoc"></a>CMap::PGetNextAssoc  
 Recupera el elemento de mapa que señala `pAssocRec`.  
  
```  
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;  
  
CPair *PGetNextAssoc(const CPair* pAssocRet);
```  
  
### <a name="parameters"></a>Parámetros  
 *pAssocRet*  
 Apunta a una entrada de mapa devuelta por una anterior [PGetNextAssoc](#pgetnextassoc) o [CMap::PGetFirstAssoc](#pgetfirstassoc) llamar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la siguiente entrada en la asignación; vea [CMap::CPair](#cpair). Si el elemento es el último de la asignación, el valor es **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para recorrer en iteración todos los elementos del mapa. Recuperar el primer elemento con una llamada a `PGetFirstAssoc` y, a continuación, recorra en iteración el mapa con las llamadas sucesivas a `PGetNextAssoc`.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMap::PGetFirstAssoc](#pgetfirstassoc).  
  
##  <a name="plookup"></a>CMap::PLookup  
 Busca el valor asignado a una clave determinada.  
  
```  
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);  
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Clave para el elemento que se va a buscar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a una estructura de clave; vea [CMap::CPair](#cpair). Si se encuentra ninguna coincidencia, `CMap::PLookup` devuelve `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para buscar un elemento de mapa con una clave que coincida exactamente con la clave dada.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]  
  
##  <a name="removeall"></a>CMap::RemoveAll  
 Quita todos los valores de esta asignación mediante una llamada a la función auxiliar global **DestructElements**.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Comentarios  
 La función funciona correctamente si el mapa ya está vacío.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]  
  
##  <a name="removekey"></a>CMap::RemoveKey  
 Busca la entrada de mapa que corresponde a la clave proporcionada; a continuación, si se encuentra la clave, quita la entrada.  
  
```  
BOOL RemoveKey(ARG_KEY key);
```  
  
### <a name="parameters"></a>Parámetros  
 `ARG_KEY`  
 Especifica el tipo de la clave de un parámetro de plantilla.  
  
 `key`  
 Clave para el elemento va a quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la entrada se encuentra y quita correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 El **DestructElements** función auxiliar se utiliza para quitar la entrada.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMap::SetAt](#setat).  
  
##  <a name="setat"></a>CMap::SetAt  
 El medio principal para insertar un elemento en un mapa.  
  
```  
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `ARG_KEY`  
 Parámetro de plantilla que especifica el tipo de la `key` parámetro.  
  
 `key`  
 Especifica la clave del nuevo elemento.  
  
 `ARG_VALUE`  
 Parámetro de plantilla que especifica el tipo de la `newValue` parámetro.  
  
 `newValue`  
 Especifica el valor del nuevo elemento.  
  
### <a name="remarks"></a>Comentarios  
 En primer lugar, se busca la clave. Si se encuentra la clave, a continuación, se cambia el valor correspondiente; en caso contrario, se crea un nuevo par de clave y valor.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC COLLECT](../../visual-cpp-samples.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)  
