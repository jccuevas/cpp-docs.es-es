---
title: Clase cObList | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CObList
- AFXCOLL/CObList
- AFXCOLL/CObList::CObList
- AFXCOLL/CObList::AddHead
- AFXCOLL/CObList::AddTail
- AFXCOLL/CObList::Find
- AFXCOLL/CObList::FindIndex
- AFXCOLL/CObList::GetAt
- AFXCOLL/CObList::GetCount
- AFXCOLL/CObList::GetHead
- AFXCOLL/CObList::GetHeadPosition
- AFXCOLL/CObList::GetNext
- AFXCOLL/CObList::GetPrev
- AFXCOLL/CObList::GetSize
- AFXCOLL/CObList::GetTail
- AFXCOLL/CObList::GetTailPosition
- AFXCOLL/CObList::InsertAfter
- AFXCOLL/CObList::InsertBefore
- AFXCOLL/CObList::IsEmpty
- AFXCOLL/CObList::RemoveAll
- AFXCOLL/CObList::RemoveAt
- AFXCOLL/CObList::RemoveHead
- AFXCOLL/CObList::RemoveTail
- AFXCOLL/CObList::SetAt
dev_langs: C++
helpviewer_keywords:
- CObList [MFC], CObList
- CObList [MFC], AddHead
- CObList [MFC], AddTail
- CObList [MFC], Find
- CObList [MFC], FindIndex
- CObList [MFC], GetAt
- CObList [MFC], GetCount
- CObList [MFC], GetHead
- CObList [MFC], GetHeadPosition
- CObList [MFC], GetNext
- CObList [MFC], GetPrev
- CObList [MFC], GetSize
- CObList [MFC], GetTail
- CObList [MFC], GetTailPosition
- CObList [MFC], InsertAfter
- CObList [MFC], InsertBefore
- CObList [MFC], IsEmpty
- CObList [MFC], RemoveAll
- CObList [MFC], RemoveAt
- CObList [MFC], RemoveHead
- CObList [MFC], RemoveTail
- CObList [MFC], SetAt
ms.assetid: 80699c93-33d8-4f8b-b8cf-7b58aeab64ca
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dfcd79377eebbf36ec4dd4688dff8b33c112e451
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="coblist-class"></a>Clase cObList
fSupports listas ordenadas de único `CObject` punteros accesibles secuencialmente o por el puntero de valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CObList : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CObList::CObList](#coblist)|Construye una lista vacía para `CObject` punteros.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CObList::AddHead](#addhead)|Agrega un elemento (o todos los elementos de otra lista) en el encabezado de la lista (hace un nuevo encabezado).|  
|[CObList::AddTail](#addtail)|Agrega un elemento (o todos los elementos de otra lista) a la cola de la lista (hace una cola nueva).|  
|[CObList::Find](#find)|Obtiene la posición de un elemento especificado por el valor del puntero.|  
|[CObList::FindIndex](#findindex)|Obtiene la posición de un elemento especificado por un índice de base cero.|  
|[CObList::GetAt](#getat)|Obtiene el elemento en una posición determinada.|  
|[CObList::GetCount](#getcount)|Devuelve el número de elementos en esta lista.|  
|[CObList::GetHead](#gethead)|Devuelve el elemento principal de la lista (no puede estar vacía).|  
|[CObList::GetHeadPosition](#getheadposition)|Devuelve la posición del elemento principal de la lista.|  
|[CObList::GetNext](#getnext)|Obtiene el elemento siguiente para efectuar una iteración.|  
|[CObList::GetPrev](#getprev)|Obtiene el elemento anterior para efectuar una iteración.|  
|[CObList::GetSize](#getsize)|Devuelve el número de elementos en esta lista.|  
|[CObList::GetTail](#gettail)|Devuelve el elemento final de la lista (no puede estar vacía).|  
|[CObList::GetTailPosition](#gettailposition)|Devuelve la posición del elemento final de la lista.|  
|[CObList::InsertAfter](#insertafter)|Inserta un nuevo elemento después de una posición especificada.|  
|[CObList::InsertBefore](#insertbefore)|Inserta un nuevo elemento antes de una posición especificada.|  
|[CObList::IsEmpty](#isempty)|Comprueba si la condición de la lista vacía (no hay elementos).|  
|[CObList::RemoveAll](#removeall)|Quita todos los elementos de esta lista.|  
|[CObList::RemoveAt](#removeat)|Quita un elemento de esta lista, especificada por posición.|  
|[CObList::RemoveHead](#removehead)|Quita el elemento del encabezado de la lista.|  
|[CObList::RemoveTail](#removetail)|Quita el elemento de la cola de la lista.|  
|[CObList::SetAt](#setat)|Establece el elemento en una posición determinada.|  
  
## <a name="remarks"></a>Comentarios  
 `CObList`las listas se comportan como listas doblemente vinculadas.  
  
 Una variable de tipo **posición** es una clave para la lista. Puede usar un **posición** variable como un iterador para recorrer una lista de forma secuencial y como un marcador que se va a contener un lugar. Una posición no es lo mismo que un índice, sin embargo.  
  
 Inserción de elementos es muy rápido en el encabezado de la lista, en la cola y en un conocido **posición**. Una búsqueda secuencial es necesaria buscar un elemento por valor o por índice. Esta búsqueda puede ser lenta si la lista es larga.  
  
 `CObList` incorpora la macro `IMPLEMENT_SERIAL` para admitir la serialización y el volcado de sus elementos. Si es una lista de `CObject` punteros se almacena en un archivo, con un operador de inserción sobrecargado o con el `Serialize` miembro funcione, cada uno de ellos `CObject` elemento se serializa a su vez.  
  
 Si se necesita un volcado de persona `CObject` elementos en la lista, debe establecer la profundidad del contexto de volcado en 1 o mayor.  
  
 Cuando un `CObList` se elimina el objeto, o cuando se quitan sus elementos, solo la `CObject` se quitan los punteros, no los objetos que hacen referencia.  
  
 Puede derivar sus propias clases de `CObList`. La nueva clase de lista, diseñada para almacenar punteros a objetos derivados de `CObject`, agrega nuevos miembros de datos y nuevas funciones de miembro. Tenga en cuenta que la lista resultante no es estrictamente tipo seguro, ya que permite la inserción de cualquier `CObject` puntero.  
  
> [!NOTE]
>  Debe utilizar el [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro en la implementación de la clase derivada si va a serializar la lista.  
  
 Para obtener más información sobre el uso de `CObList`, vea el artículo [colecciones](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CObList`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcoll.h  
  
##  <a name="addhead"></a>CObList::AddHead  
 Agrega un nuevo elemento o una lista de elementos en el encabezado de esta lista.  
  
```  
POSITION AddHead(CObject* newElement);  
void AddHead(CObList* pNewList);
```  
  
### <a name="parameters"></a>Parámetros  
 `newElement`  
 El `CObject` puntero va a agregar a esta lista.  
  
 `pNewList`  
 Un puntero a otro `CObList` lista. Los elementos de `pNewList` se agregará a esta lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la primera versión del **posición** valor del elemento recién insertado.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::AddHead`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSICIÓN AddHead (void\***  `newElement` **);**<br /><br /> **void AddHead (CPtrList\***  `pNewList` **);**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**POSICIÓN AddHead (const CString &** `newElement` **);**<br /><br /> **POSICIÓN AddHead (LPCTSTR** `newElement` **);**<br /><br /> **void AddHead (objeto CStringList\***  `pNewList` **);**|  
  
### <a name="remarks"></a>Comentarios  
 La lista puede estar vacía antes de la operación.  
  
### <a name="example"></a>Ejemplo  
  Vea [CObList::CObList](#coblist) para obtener una lista de los `CAge` clase.  
  
 [!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]  
  
 Los resultados de este programa son los siguientes:  
  
 `AddHead example: A CObList with 2 elements`  
  
 `a CAge at $44A8 40`  
  
 `a CAge at $442A 21`  
  
##  <a name="addtail"></a>CObList::AddTail  
 Agrega un nuevo elemento o una lista de elementos a la cola de esta lista.  
  
```  
POSITION AddTail(CObject* newElement);  
void AddTail(CObList* pNewList);
```  
  
### <a name="parameters"></a>Parámetros  
 `newElement`  
 El `CObject` puntero va a agregar a esta lista.  
  
 `pNewList`  
 Un puntero a otro `CObList` lista. Los elementos de `pNewList` se agregará a esta lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la primera versión del **posición** valor del elemento recién insertado.  
  
### <a name="remarks"></a>Comentarios  
 La lista puede estar vacía antes de la operación.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::AddTail`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSICIÓN AddTail (void\***  `newElement` **);**<br /><br /> **void AddTail (CPtrList\***  `pNewList` **);**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**POSICIÓN AddTail (const CString &** `newElement` **);**<br /><br /> **POSICIÓN AddTail (LPCTSTR** `newElement` **);**<br /><br /> **void AddTail (objeto CStringList\***  `pNewList` **);**|  
  
### <a name="example"></a>Ejemplo  
  Vea [CObList::CObList](#coblist) para obtener una lista de los `CAge` clase.  
  
 [!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]  
  
 Los resultados de este programa son los siguientes:  
  
 `AddTail example: A CObList with 2 elements`  
  
 `a CAge at $444A 21`  
  
 `a CAge at $4526 40`  
  
##  <a name="coblist"></a>CObList::CObList  
 Construye un vacío `CObject` lista de puntero.  
  
```  
CObList(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>Parámetros  
 `nBlockSize`  
 La granularidad de asignación de memoria para ampliar la lista.  
  
### <a name="remarks"></a>Comentarios  
 A medida que crece la lista, se asigna memoria en unidades de `nBlockSize` entradas. Si se produce un error en una asignación de memoria, un `CMemoryException` se produce.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::CObList`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList (INT_PTR** `nBlockSize` **= 10);**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**Objeto CStringList (INT_PTR** `nBlockSize` **= 10);**|  
  
### <a name="example"></a>Ejemplo  
  A continuación se muestra una lista de los `CObject`-clase derivada `CAge` utiliza en todos los ejemplos de la colección:  
  
 [!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]  
  
 A continuación se muestra un ejemplo de `CObList` uso de constructor:  
  
 [!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]  
  
##  <a name="find"></a>CObList::Find  
 Busca en la lista secuencialmente para buscar el primer extremo `CObject` puntero coincidencia especificado `CObject` puntero.  
  
```  
POSITION Find(
    CObject* searchValue,  
    POSITION startAfter = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `searchValue`  
 El puntero de objeto que se encuentren en esta lista.  
  
 `startAfter`  
 La posición inicial de la búsqueda.  
  
### <a name="return-value"></a>Valor devuelto  
 A **posición** valor que se puede usar para la iteración o recuperación de puntero de objeto; **NULL** si no se encuentra el objeto.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que se comparan los valores de puntero, no el contenido de los objetos.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::Find`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Búsqueda de posición (void\***  `searchValue` **, posición** `startAfter` **= NULL) const;**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**Búsqueda de posición (LPCTSTR** `searchValue` **, posición** `startAfter` **= NULL) const;**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](#coblist) para obtener una lista de los `CAge` clase.  
  
 [!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]  
  
##  <a name="findindex"></a>CObList::FindIndex  
 Utiliza el valor de `nIndex` como un índice en la lista.  
  
```  
POSITION FindIndex(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de base cero del elemento de lista que se encuentra.  
  
### <a name="return-value"></a>Valor devuelto  
 A **posición** valor que se puede usar para la iteración o recuperación de puntero de objeto; **NULL** si `nIndex` es demasiado grande. (El marco de trabajo genera una aserción si `nIndex` es negativo.)  
  
### <a name="remarks"></a>Comentarios  
 Iniciar un examen secuencial desde el principio de la lista, detener la  *n* elemento th.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::FindIndex`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSICIÓN FindIndex (INT_PTR** `nIndex` **) const;**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**POSICIÓN FindIndex (INT_PTR** `nIndex` **) const;**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](#coblist) para obtener una lista de los `CAge` clase.  
  
 [!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]  
  
##  <a name="getat"></a>CObList::GetAt  
 Una variable de tipo **posición** es una clave para la lista.  
  
```  
CObject*& GetAt(POSITION position);  
const CObject*& GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *posición*  
 A **posición** valor devuelto por un anterior `GetHeadPosition` o **buscar** llamada a función miembro.  
  
### <a name="return-value"></a>Valor devuelto  
 Vea la descripción de valor devuelto de [GetHead](#gethead).  
  
### <a name="remarks"></a>Comentarios  
 No es lo mismo que un índice, y no puede funcionar en un **posición** valor usted mismo. `GetAt`Recupera el `CObject` puntero asociado a una posición especificada.  
  
 Debe asegurarse de que su **posición** valor representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::GetAt`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Const void\*& GetAt (posición** *posición* **) const;**<br /><br /> **void\*& GetAt (posición** *posición* **);**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetAt (posición** *posición* **) const;**<br /><br /> **CString & GetAt (posición** *posición* **);**|  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [FindIndex](#findindex).  
  
##  <a name="getcount"></a>CObList::GetCount  
 Obtiene el número de elementos en esta lista.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Valor entero que contiene el número de elementos.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::GetCount`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount () const;**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount () const;**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](#coblist) para obtener una lista de los `CAge` clase.  
  
 [!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]  
  
##  <a name="gethead"></a>CObList::GetHead  
 Obtiene el `CObject` puntero que representa el elemento principal de esta lista.  
  
```  
CObject*& GetHead();  
const CObject*& GetHead() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se tiene acceso a la lista mediante un puntero a un **CObList const**, a continuación, `GetHead` devuelve un `CObject` puntero. Esto permite la función que se va a usarse solo en el lado derecho de una instrucción de asignación y, por tanto, protege la lista frente a modificaciones.  
  
 Si se tiene acceso a la lista directamente o a través de un puntero a un `CObList`, a continuación, `GetHead` devuelve una referencia a un `CObject` puntero. Esto permite la función que se utilizará en cada lado de una instrucción de asignación y, por tanto, permite que las entradas de lista a modificarse.  
  
### <a name="remarks"></a>Comentarios  
 Debe asegurarse de que la lista no está vacía antes de llamar a `GetHead`. Si la lista está vacía, se valida la versión de depuración de la biblioteca Microsoft Foundation Class. Use [IsEmpty](#isempty) para comprobar que la lista contiene elementos.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::GetHead`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Const void\*& () GetHead const; void\*& GetHead ();**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetHead () const; (De CString & GetHead);**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](#coblist) para obtener una lista de los `CAge` clase.  
  
 En el ejemplo siguiente se muestra el uso de `GetHead` en el lado izquierdo de una instrucción de asignación.  
  
 [!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]  
  
##  <a name="getheadposition"></a>CObList::GetHeadPosition  
 Obtiene la posición del elemento principal de esta lista.  
  
```  
POSITION GetHeadPosition() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 A **posición** valor que se puede usar para la iteración o recuperación de puntero de objeto; **NULL** si la lista está vacía.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::GetHeadPosition`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**(Posición GetHeadPosition) const;**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**(Posición GetHeadPosition) const;**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](#coblist) para obtener una lista de los `CAge` clase.  
  
 [!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]  
  
##  <a name="getnext"></a>CObList::GetNext  
 Obtiene el elemento de lista identificado por `rPosition`, a continuación, establece `rPosition` a la `POSITION` valor de la entrada siguiente en la lista.  
  
```  
CObject*& GetNext(POSITION& rPosition);  
const CObject* GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `rPosition`  
 Una referencia a un `POSITION` valor devuelto por un anterior `GetNext`, `GetHeadPosition`, u otra llamada de función miembro.  
  
### <a name="return-value"></a>Valor devuelto  
 Vea la descripción de valor devuelto de [GetHead](#gethead).  
  
### <a name="remarks"></a>Comentarios  
 Puede usar `GetNext` en un bucle de iteración de avance, si establece la posición inicial con una llamada a `GetHeadPosition` o `Find`.  
  
 Debe asegurarse de que su `POSITION` valor representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.  
  
 Si el elemento recuperado es el último en la lista, a continuación, el nuevo valor de `rPosition` está establecido en `NULL`.  
  
 Es posible quitar un elemento durante una iteración. Vea el ejemplo de [RemoveAt](#removeat).  
  
> [!NOTE]
>  A partir de MFC 8.0 ha cambiado la versión const de este método para devolver `const CObject*` en lugar de `const CObject*&`.  Este cambio se realizó para poner el compilador en conformidad con el estándar de C++.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::GetNext`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|  
  
### <a name="example"></a>Ejemplo  
  Vea [CObList::CObList](#coblist) para obtener una lista de los `CAge` clase.  
  
 [!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]  
  
 Los resultados de este programa son los siguientes:  
  
 `a CAge at $479C 40`  
  
 `a CAge at $46C0 21`  
  
##  <a name="getprev"></a>CObList::GetPrev  
 Obtiene el elemento de lista identificado por `rPosition`, a continuación, establece `rPosition` a la `POSITION` valor de la entrada anterior en la lista.  
  
```  
CObject*& GetPrev(POSITION& rPosition);  
const CObject* GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `rPosition`  
 Una referencia a un `POSITION` valor devuelto por un anterior `GetPrev` u otra llamada de función miembro.  
  
### <a name="return-value"></a>Valor devuelto  
 Vea la descripción de valor devuelto de [GetHead](#gethead).  
  
### <a name="remarks"></a>Comentarios  
 Puede usar `GetPrev` en un bucle de iteración inversa si establece la posición inicial con una llamada a `GetTailPosition` o `Find`.  
  
 Debe asegurarse de que su `POSITION` valor representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.  
  
 Si el elemento recuperado es el primer elemento de la lista, a continuación, el nuevo valor de `rPosition` está establecido en `NULL`.  
  
> [!NOTE]
>  A partir de MFC 8.0 ha cambiado la versión const de este método para devolver `const CObject*` en lugar de `const CObject*&`.  Este cambio se realizó para poner el compilador en conformidad con el estándar de C++.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::GetPrev`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|  
  
### <a name="example"></a>Ejemplo  
  Vea [CObList::CObList](#coblist) para obtener una lista de los `CAge` clase.  
  
 [!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]  
  
 Los resultados de este programa son los siguientes:  
  
 `a CAge at $421C 21`  
  
 `a CAge at $421C 40`  
  
##  <a name="getsize"></a>CObList::GetSize  
 Devuelve el número de elementos de lista.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de elementos de la lista.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para recuperar el número de elementos de la lista.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::GetSize`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetSize () const;**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetSize () const;**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](#coblist) para obtener una lista de los `CAge` clase.  
  
 [!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]  
  
##  <a name="gettail"></a>CObList::GetTail  
 Obtiene el `CObject` puntero que representa el elemento final de esta lista.  
  
```  
CObject*& GetTail();  
const CObject*& GetTail() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Vea la descripción de valor devuelto de [GetHead](#gethead).  
  
### <a name="remarks"></a>Comentarios  
 Debe asegurarse de que la lista no está vacía antes de llamar a `GetTail`. Si la lista está vacía, se valida la versión de depuración de la biblioteca Microsoft Foundation Class. Use [IsEmpty](#isempty) para comprobar que la lista contiene elementos.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::GetTail`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Const void\*& () GetTail const; void\*& GetTail ();**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetTail () const; (De CString & GetTail);**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](#coblist) para obtener una lista de los `CAge` clase.  
  
 [!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]  
  
##  <a name="gettailposition"></a>CObList::GetTailPosition  
 Obtiene la posición del elemento final de esta lista; **NULL** si la lista está vacía.  
  
```  
POSITION GetTailPosition() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 A **posición** valor que se puede usar para la iteración o recuperación de puntero de objeto; **NULL** si la lista está vacía.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::GetTailPosition`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**(Posición GetTailPosition) const;**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**(Posición GetTailPosition) const;**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](#coblist) para obtener una lista de los `CAge` clase.  
  
 [!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]  
  
##  <a name="insertafter"></a>CObList::InsertAfter  
 Agrega un elemento a esta lista después del elemento en la posición especificada.  
  
```  
POSITION InsertAfter(
    POSITION position,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Parámetros  
 *posición*  
 Un valor **POSITION** devuelto por una llamada de función de miembro `GetNext`, `GetPrev`, o **Find** anterior.  
  
 `newElement`  
 Puntero de objeto que se va a agregar a esta lista.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::InsertAfter`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSICIÓN InsertAfter (posición** *posición* **, void\***  `newElement` **);**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**POSICIÓN InsertAfter (posición** *posición* **, const CString &** `newElement` **);**<br /><br /> **POSICIÓN InsertAfter (posición** *posición* **, LPCTSTR** `newElement` **);**|  
  
### <a name="return-value"></a>Valor devuelto  
 A **posición** valor que es el mismo como el *posición* parámetro.  
  
### <a name="example"></a>Ejemplo  
  Vea [CObList::CObList](#coblist) para obtener una lista de los `CAge` clase.  
  
 [!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]  
  
 Los resultados de este programa son los siguientes:  
  
 `InsertAfter example: A CObList with 3 elements`  
  
 `a CAge at $4A44 40`  
  
 `a CAge at $4A64 65`  
  
 `a CAge at $4968 21`  
  
##  <a name="insertbefore"></a>CObList::InsertBefore  
 Agrega un elemento a esta lista delante del elemento en la posición especificada.  
  
```  
POSITION InsertBefore(
    POSITION position,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Parámetros  
 *posición*  
 Un valor **POSITION** devuelto por una llamada de función de miembro `GetNext`, `GetPrev`, o **Find** anterior.  
  
 `newElement`  
 Puntero de objeto que se va a agregar a esta lista.  
  
### <a name="return-value"></a>Valor devuelto  
 A **posición** valor que se puede usar para la iteración o recuperación de puntero de objeto; **NULL** si la lista está vacía.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::InsertBefore`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSICIÓN InsertBefore (posición** *posición* **, void\***  `newElement` **);**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**POSICIÓN InsertBefore (posición** *posición* **, const CString &** `newElement` **);**<br /><br /> **POSICIÓN InsertBefore (posición** *posición* **, LPCTSTR** `newElement` **);**|  
  
### <a name="example"></a>Ejemplo  
  Vea [CObList::CObList](#coblist) para obtener una lista de los `CAge` clase.  
  
 [!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]  
  
 Los resultados de este programa son los siguientes:  
  
 `InsertBefore example: A CObList with 3 elements`  
  
 `a CAge at $4AE2 40`  
  
 `a CAge at $4B02 65`  
  
 `a CAge at $49E6 21`  
  
##  <a name="isempty"></a>CObList::IsEmpty  
 Indica si esta lista no contiene elementos.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si esta lista está vacía. en caso contrario es 0.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::IsEmpty`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**BOOL IsEmpty () const;**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**BOOL IsEmpty () const;**|  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [RemoveAll](#removeall).  
  
##  <a name="removeall"></a>CObList::RemoveAll  
 Quita todos los elementos de esta lista y se liberan asociado `CObList` memoria.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Comentarios  
 Si la lista está vacía, se genera ningún error.  
  
 Al quitar elementos de un `CObList`, quite los punteros a objetos de la lista. Es responsabilidad suya eliminar los propios objetos.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::RemoveAll`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAll ();**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAll ();**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](#coblist) para obtener una lista de los `CAge` clase.  
  
 [!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]  
  
##  <a name="removeat"></a>CObList::RemoveAt  
 Quita el elemento especificado de esta lista.  
  
```  
void RemoveAt(POSITION position);
```  
  
### <a name="parameters"></a>Parámetros  
 *posición*  
 La posición del elemento que se va a quitar de la lista.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se quita un elemento de un `CObList`, quite el puntero de objeto de la lista. Es responsabilidad suya eliminar los propios objetos.  
  
 Debe asegurarse de que su **posición** valor representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::RemoveAt`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAt (posición** *posición* **);**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAt (posición** *posición* **);**|  
  
### <a name="example"></a>Ejemplo  
  Tenga cuidado al quitar un elemento durante una iteración de la lista. En el ejemplo siguiente se muestra una técnica de eliminación que garantiza un válido **posición** valor [GetNext](#getnext).  
  
 Vea [CObList::CObList](#coblist) para obtener una lista de los `CAge` clase.  
  
 [!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]  
  
 Los resultados de este programa son los siguientes:  
  
 `RemoveAt example: A CObList with 2 elements`  
  
 `a CAge at $4C1E 65`  
  
 `a CAge at $4B22 21`  
  
##  <a name="removehead"></a>CObList::RemoveHead  
 Quita el elemento del encabezado de la lista y devuelve un puntero a ella.  
  
```  
CObject* RemoveHead();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El `CObject` puntero previamente al principio de la lista.  
  
### <a name="remarks"></a>Comentarios  
 Debe asegurarse de que la lista no está vacía antes de llamar a `RemoveHead`. Si la lista está vacía, se valida la versión de depuración de la biblioteca Microsoft Foundation Class. Use [IsEmpty](#isempty) para comprobar que la lista contiene elementos.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::RemoveHead`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead ();**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveHead ();**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](#coblist) para obtener una lista de los `CAge` clase.  
  
 [!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]  
  
##  <a name="removetail"></a>CObList::RemoveTail  
 Quita el elemento de la cola de la lista y devuelve un puntero a ella.  
  
```  
CObject* RemoveTail();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto al que estaba en la cola de la lista.  
  
### <a name="remarks"></a>Comentarios  
 Debe asegurarse de que la lista no está vacía antes de llamar a `RemoveTail`. Si la lista está vacía, se valida la versión de depuración de la biblioteca Microsoft Foundation Class. Use [IsEmpty](#isempty) para comprobar que la lista contiene elementos.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::RemoveTail`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveTail ();**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveTail ();**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](#coblist) para obtener una lista de los `CAge` clase.  
  
 [!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]  
  
##  <a name="setat"></a>CObList::SetAt  
 Establece el elemento en una posición determinada.  
  
```  
void SetAt(
    POSITION pos,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El **posición** del elemento que se va a establecer.  
  
 `newElement`  
 El `CObject` puntero se escriban en la lista.  
  
### <a name="remarks"></a>Comentarios  
 Una variable de tipo **posición** es una clave para la lista. No es lo mismo que un índice, y no puede funcionar en un **posición** valor usted mismo. `SetAt`Escribe el `CObject` puntero a la posición especificada en la lista.  
  
 Debe asegurarse de que su **posición** valor representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObList::SetAt`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void SetAt (posición** `pos` **, const CString &** `newElement` **);**|  
|[Objeto CStringList](../../mfc/reference/cstringlist-class.md)|**void SetAt (posición** `pos` **, LPCTSTR** `newElement` **);**|  
  
### <a name="example"></a>Ejemplo  
  Vea [CObList::CObList](#coblist) para obtener una lista de los `CAge` clase.  
  
 [!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]  
  
 Los resultados de este programa son los siguientes:  
  
 `SetAt example: A CObList with 2 elements`  
  
 `a CAge at $4D98 40`  
  
 `a CAge at $4DB8 65`  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clase de objeto CStringList](../../mfc/reference/cstringlist-class.md)   
 [CPtrList (clase)](../../mfc/reference/cptrlist-class.md)
