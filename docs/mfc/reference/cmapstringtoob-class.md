---
title: Clase CMapStringToOb | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMapStringToOb
- AFXCOLL/CMapStringToOb
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
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
dev_langs: C++
helpviewer_keywords:
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: 09653980-b885-4f3a-8594-0aeb7f94c601
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1a840677819710247e73aa8e3bcb904be756f852
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmapstringtoob-class"></a>Clase CMapStringToOb
Una clase de colección de diccionarios que asigna objetos `CString` únicos a punteros `CObject` .  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMapStringToOb : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMapStringToOb::CMapStringToOb](#cmapstringtoob)|Constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMapStringToOb::GetCount](#getcount)|Devuelve el número de elementos de esta asignación.|  
|[CMapStringToOb::GetHashTableSize](#gethashtablesize)|Determina el número actual de elementos de la tabla hash.|  
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|Obtiene el elemento siguiente para efectuar una iteración.|  
|[CMapStringToOb::GetSize](#getsize)|Devuelve el número de elementos de esta asignación.|  
|[CMapStringToOb::GetStartPosition](#getstartposition)|Devuelve la posición del primer elemento.|  
|[CMapStringToOb::HashKey](#hashkey)|Calcula el valor hash de una clave especificada.|  
|[CMapStringToOb::InitHashTable](#inithashtable)|Inicializa la tabla hash.|  
|[CMapStringToOb::IsEmpty](#isempty)|Comprueba si la condición de mapa está vacío (no hay elementos).|  
|[CMapStringToOb::Lookup](#lookup)|Busca un puntero void en función de la clave de puntero void. El valor del puntero, no la entidad que señala, se utiliza para la comparación de claves.|  
|[CMapStringToOb::LookupKey](#lookupkey)|Devuelve una referencia a la clave asociada con el valor de clave especificado.|  
|[CMapStringToOb::RemoveAll](#removeall)|Quita todos los elementos de esta asignación.|  
|[CMapStringToOb::RemoveKey](#removekey)|Quita un elemento especificado por una clave.|  
|[CMapStringToOb::SetAt](#setat)|Inserta un elemento en la asignación; reemplaza un elemento existente si se encuentra una clave coincidente.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[[] CMapStringToOb::operator](#operator_at)|Inserta un elemento en el mapa: sustitución de operador para `SetAt`.|  
  
## <a name="remarks"></a>Comentarios  
 Una vez que ha insertado un `CString` -  `CObject*` par (elemento) en el mapa, eficazmente puede recuperar o eliminar el par con una cadena o un `CString` valor como una clave. También puede iterar por todos los elementos del mapa.  
  
 Una variable de tipo **posición** se usa para el acceso de entrada alternativo en todas las variaciones de mapa. Puede usar un **posición** "recordar" una entrada y para recorrer en iteración el mapa. Puede que piense que esta iteración es secuencial por valor de clave; no es así. La secuencia de elementos recuperados es indeterminada.  
  
 `CMapStringToOb` incorpora la macro `IMPLEMENT_SERIAL` para admitir la serialización y el volcado de sus elementos. Cada elemento se serializa a su vez si una asignación se almacena en un archivo, ya sea con la inserción sobrecargada (  **<<** ) operador o con el `Serialize` función miembro.  
  
 Si se necesita un volcado de diagnóstico de los elementos individuales de la asignación (la `CString` valor y el `CObject` contenido), debe establecer la profundidad del contexto de volcado en 1 o mayor.  
  
 Cuando un `CMapStringToOb` se elimina el objeto, o cuando se quitan sus elementos, el `CString` objetos y `CObject` se quitan los punteros. Los objetos al que hace referencia el `CObject` punteros no se destruyen.  
  
 Derivación de la clase Map es similar a la derivación de la lista. Vea el artículo [colecciones](../../mfc/collections.md) para ver una ilustración de la derivación de una clase de lista de propósito especial.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToOb`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcoll.h  
  
##  <a name="cmapstringtoob"></a>CMapStringToOb::CMapStringToOb  
 Construye un vacío `CString`- a - `CObject*` mapa.  
  
```  
CMapStringToOb(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>Parámetros  
 `nBlockSize`  
 Especifica la granularidad de asignación de memoria para extender la asignación.  
  
### <a name="remarks"></a>Comentarios  
 A medida que aumenta la asignación, se asigna memoria en unidades de `nBlockSize` entradas.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a **CMapStringToOb:: CMapStringToOb**.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr (INT_PTR** `nBlockSize` **= 10);**|  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]  
  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
##  <a name="getcount"></a>CMapStringToOb::GetCount  
 Determina cuántos elementos se encuentran en el mapa.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos de esta asignación.  
  
### <a name="remarks"></a>Comentarios  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CMapStringToOb::GetCount`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetCount () const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetCount () const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetCount () const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetCount () const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetCount () const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetCount () const;**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]  
  
##  <a name="gethashtablesize"></a>CMapStringToOb::GetHashTableSize  
 Determina el número actual de elementos de la tabla hash.  
  
```  
UINT GetHashTableSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de elementos en la tabla hash.  
  
### <a name="remarks"></a>Comentarios  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CMapStringToOb::GetHashTableSize`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT () de GetHashTableSize const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT () de GetHashTableSize const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT () de GetHashTableSize const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT () de GetHashTableSize const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT () de GetHashTableSize const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT () de GetHashTableSize const;**|  
  
##  <a name="getnextassoc"></a>CMapStringToOb::GetNextAssoc  
 Recupera el elemento de mapa en *rNextPosition*, a continuación, actualiza *rNextPosition* para hacer referencia al elemento siguiente en el mapa.  
  
```  
void GetNextAssoc(
    POSITION& rNextPosition,  
    CString& rKey,  
    CObject*& rValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *rNextPosition*  
 Especifica una referencia a un **posición** valor devuelto por un anterior **GetNextAssoc** o **GetStartPosition** llamar.  
  
 *rKey*  
 Especifica la clave devuelta del elemento recuperado (una cadena).  
  
 *valor r*  
 Especifica el valor devuelto del elemento recuperado (un **CObject** puntero). Vea la sección Comentarios para obtener más información acerca de este parámetro.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es muy útil para recorrer en iteración todos los elementos del mapa. Tenga en cuenta que la secuencia de posición no es necesariamente el mismo que la secuencia de valores de clave.  
  
 Si el elemento recuperado es el último en el mapa, a continuación, el nuevo valor de *rNextPosition* está establecido en **NULL**.  
  
 Para el *rValue* parámetro, no olvide convierte el tipo de objeto para **CObject\*&**, que es lo que el compilador requiere, como se muestra en el ejemplo siguiente:  
  
 [!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]  
  
 Esto no es cierto **GetNextAssoc** para mapas basados en plantillas.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a **CMapStringToOb::GetNextAssoc**.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc (posición &** *rNextPosition* **, void\* &**  *rKey* **, void\* &**  *rValue* **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc (posición &** *rNextPosition* **, void\* &**  *rKey* **, WORD &** *rValue* **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc (posición &** *rNextPosition* **, CString &** *rKey* **, void\* &**  *rValue* **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc (posición &** *rNextPosition* **, CString &** *rKey* **, CString &** *rValue* **) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc (posición &** *rNextPosition* **, WORD &** *rKey* **, CObject\* &**  *rValue* **) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc (posición &** *rNextPosition* **, WORD &** *rKey* **, void\* &**  *rValue* **) const;**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]  
  
 Los resultados de este programa son los siguientes:  
  
 `Lisa : a CAge at $4724 11`  
  
 `Marge : a CAge at $47A8 35`  
  
 `Homer : a CAge at $4766 36`  
  
 `Bart : a CAge at $45D4 13`  
  
##  <a name="getsize"></a>CMapStringToOb::GetSize  
 Devuelve el número de elementos de mapa.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos en el mapa.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para recuperar el número de elementos en el mapa.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CMapStringToOb::GetSize`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetSize () const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetSize () const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetSize () const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetSize () const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetSize () const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetSize () const;**|  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]  
  
##  <a name="getstartposition"></a>CMapStringToOb::GetStartPosition  
 Inicie una iteración de mapa devolviendo un **posición** valor que se puede pasar a un `GetNextAssoc` llamar a.  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 A **posición** valor que indica una posición inicial para efectuar una iteración del objeto map; o **NULL** si el mapa está vacío.  
  
### <a name="remarks"></a>Comentarios  
 La secuencia de la iteración no es de predicción; por lo tanto, el "primer elemento en el mapa" no tiene ninguna importancia especial.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CMapStringToOb::GetStartPosition`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**(Posición GetHeadPosition) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**(Posición GetHeadPosition) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**(Posición GetHeadPosition) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**(Posición GetHeadPosition) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**(Posición GetHeadPosition) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**(Posición GetHeadPosition) const;**|  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CMapStringToOb::GetNextAssoc](#getnextassoc).  
  
##  <a name="hashkey"></a>CMapStringToOb::HashKey  
 Calcula el valor hash de una clave especificada.  
  
```  
UINT HashKey(LPCTSTR key) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 La clave cuyo valor de hash se va a calcular.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de clave hash  
  
### <a name="remarks"></a>Comentarios  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CMapStringToOb::HashKey`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT HashKey (void\***  `key` **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT HashKey (void\***  `key` **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT HashKey (LPCTSTR** `key` **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT HashKey (LPCTSTR** `key` **) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**HashKey UINT (palabra** `key` **) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**HashKey UINT (palabra** `key` **) const;**|  
  
##  <a name="inithashtable"></a>CMapStringToOb::InitHashTable  
 Inicializa la tabla hash.  
  
```  
void InitHashTable(
    UINT hashSize,  
    BOOL bAllocNow = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `hashSize`  
 Número de entradas en la tabla hash.  
  
 `bAllocNow`  
 Si **TRUE**, asigna la tabla hash en la inicialización; en caso contrario, se asigna a la tabla cuando sea necesario.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener el mejor rendimiento, el tamaño de la tabla hash debe ser un número primo. Para minimizar los conflictos, el tamaño debe ser aproximadamente 20 por ciento mayor que el conjunto de datos previsto más grande.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CMapStringToOb::InitHashTable`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
  
##  <a name="isempty"></a>CMapStringToOb::IsEmpty  
 Determina si el mapa está vacío.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si esta asignación no contiene elementos; en caso contrario es 0.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [RemoveAll](#removeall).  
  
### <a name="remarks"></a>Comentarios  
 En la tabla siguiente se muestra otro miembro funciones que son similares a **CMapStringToOb:: IsEmpty**.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL IsEmpty () const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL IsEmpty () const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL IsEmpty () const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL IsEmpty () const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL IsEmpty () const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL IsEmpty () const;**|  
  
##  <a name="lookup"></a>CMapStringToOb::Lookup  
 Devuelve un `CObject` basados en punteros en un `CString` valor.  
  
```  
BOOL Lookup(
    LPCTSTR key,  
    CObject*& rValue) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Especifica la clave de cadena que identifica el elemento que se va a buscar.  
  
 `rValue`  
 Especifica el valor devuelto desde el elemento buscado.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se encontró el elemento; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 `Lookup`aplica un algoritmo hash para encontrar rápidamente el elemento de mapa con una clave que coincide exactamente ( `CString` valor).  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CMapStringToOb::LookUp`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Búsqueda de BOOL (void\***  `key` **, void\* &**  `rValue` **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Búsqueda de BOOL (void\***  `key` **, WORD &** `rValue` **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Búsqueda de BOOL (LPCTSTR** `key` **, void\* &**  `rValue` **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Búsqueda de BOOL (LPCTSTR** `key` **, CString &** `rValue` **) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Búsqueda de BOOL (palabra** `key` **, CObject\* &**  `rValue` **) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Búsqueda de BOOL (palabra** `key` **, void\* &**  `rValue` **) const;**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]  
  
##  <a name="lookupkey"></a>CMapStringToOb::LookupKey  
 Devuelve una referencia a la clave asociada con el valor de clave especificado.  
  
```  
BOOL LookupKey(
    LPCTSTR key,  
    LPCTSTR& rKey) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Especifica la clave de cadena que identifica el elemento que se va a buscar.  
  
 `rKey`  
 La referencia a la clave asociada.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se encuentra la clave; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Utilizando una referencia a una clave no es seguro si utilizar una vez que el elemento asociado se quita de la asignación o después de que se destruya el mapa.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a **CMapStringToOb:: LookupKey**.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL LookupKey (LPCTSTR** `key` **, LPCTSTR &** `rKey` **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL LookupKey (LPCTSTR** `key` **, LPCTSTR &** `rKey` **) const;**|  
  
##  <a name="operator_at"></a>[] CMapStringToOb::operator  
 Un sustituto adecuado para la `SetAt` función miembro.  
  
```  
CObject*& operator[ ](lpctstr key);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a un puntero a un `CObject` objeto; o **NULL** si el mapa está vacío o `key` está fuera del intervalo.  
  
### <a name="remarks"></a>Comentarios  
 Lo que se puede utilizar sólo en el lado izquierdo de una instrucción de asignación (un valor l). Si no hay ningún elemento de mapa con la clave especificada, se crea un nuevo elemento.  
  
 No hay ningún "derecha" (valor r) equivalente a este operador porque es posible que no se puede encontrar una clave en el mapa. Use la `Lookup` función de miembro para la recuperación de elemento.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a **[] CMapStringToOb::operator**.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void\*& operator [] (void\***  `key`  **\);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**WORD & (operador) [] (void\***  `key`  **\);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void\*& operator [] (lpctstr** `key`  **\);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString & (operador) [] (lpctstr** `key`  **\);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*& operator [] (word** `key`  **\);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void\*& operator [] (word** `key`  **\);**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]  
  
 Los resultados de este programa son los siguientes:  
  
 `Operator [] example: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $4A02 11`  
  
 `[Bart] = a CAge at $497E 13`  
  
##  <a name="removeall"></a>CMapStringToOb::RemoveAll  
 Quita todos los elementos de esta asignación y se destruye el `CString` objetos de clave.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Comentarios  
 El `CObject` no se destruyen objetos referenciados por cada clave. El `RemoveAll` función puede ocasionar pérdidas de memoria si no está seguro de que la que hace referencia `CObject` objetos se destruyen.  
  
 La función funciona correctamente si el mapa ya está vacío.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CMapStringToOb::RemoveAll`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll ();**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll ();**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll ();**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll ();**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll ();**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll ();**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]  
  
##  <a name="removekey"></a>CMapStringToOb::RemoveKey  
 Busca la entrada de mapa que corresponde a la clave proporcionada; a continuación, si se encuentra la clave, quita la entrada.  
  
```  
BOOL RemoveKey(LPCTSTR key);
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Especifica la cadena que se usan para la búsqueda de mapa.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la entrada se encuentra y quita correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esto puede causar pérdidas de memoria si el `CObject` objeto no se elimina en otro lugar.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CMapStringToOb::RemoveKey`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL RemoveKey (void\***  `key` **);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL RemoveKey (void\***  `key` **);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL RemoveKey (WORD** `key` **);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL RemoveKey (WORD** `key` **);**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]  
  
 Los resultados de este programa son los siguientes:  
  
 `RemoveKey example: A CMapStringToOb with 3 elements`  
  
 `[Marge] = a CAge at $49A0 35`  
  
 `[Homer] = a CAge at $495E 36`  
  
 `[Bart] = a CAge at $4634 13`  
  
##  <a name="setat"></a>CMapStringToOb::SetAt  
 El medio principal para insertar un elemento en un mapa.  
  
```  
void SetAt(
    LPCTSTR key,  
    CObject* newValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Especifica la cadena que es la clave del nuevo elemento.  
  
 `newValue`  
 Especifica el `CObject` puntero que es el valor del nuevo elemento.  
  
### <a name="remarks"></a>Comentarios  
 En primer lugar, se busca la clave. Si se encuentra la clave, a continuación, se cambia el valor correspondiente; en caso contrario, se crea un nuevo elemento de clave y valor.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CMapStringToOb::SetAt`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void SetAt (void\***  `key` **, void\***  `newValue` **);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void SetAt (void\***  `key` **, WORD** `newValue` **);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void SetAt (LPCTSTR** `key` **, void\***  `newValue` **);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void SetAt (LPCTSTR** `key` **, LPCTSTR** `newValue` **);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void SetAt (WORD** `key` **, CObject\***  `newValue` **);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void SetAt (WORD** `key` **, void\***  `newValue` **);**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]  
  
 Los resultados de este programa son los siguientes:  
  
 `before Lisa's birthday: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $493C 11`  
  
 `[Bart] = a CAge at $4654 13`  
  
 `after Lisa's birthday: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $49C0 12`  
  
 `[Bart] = a CAge at $4654 13`  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clase CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)   
 [Clase CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)   
 [Clase CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)   
 [Clase CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)   
 [Clase CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)   
 [CMapWordToPtr (clase)](../../mfc/reference/cmapwordtoptr-class.md)
