---
title: Clase CObArray | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CObArray
- AFXCOLL/CObArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
dev_langs:
- C++
helpviewer_keywords:
- arrays [C++], pointers
- CObArray class
- arrays [C++], Object type
- object arrays, CObArray class
ms.assetid: 27894efd-2370-4776-9ed9-24a98492af17
caps.latest.revision: 20
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 90e95f10a2dc183734255e94a5ebe1d582bb026f
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="cobarray-class"></a>CObArray (clase)
Admite matrices de punteros `CObject` .  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CObArray : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CObArray::CObArray](#cobarray)|Construye una matriz vacía para `CObject` punteros.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CObArray::Add](#add)|Agrega un elemento al final de la matriz; aumenta el tamaño de la matriz si es necesario.|  
|[CObArray::Append](#append)|Anexa otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|  
|[CObArray::Copy](#copy)|Copia otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|  
|[CObArray::ElementAt](#elementat)|Devuelve una referencia temporal al puntero del elemento dentro de la matriz.|  
|[CObArray::FreeExtra](#freeextra)|Libera toda la memoria no usada por encima del límite superior actual.|  
|[CObArray::GetAt](#getat)|Devuelve el valor en un índice dado.|  
|[CObArray::GetCount](#getcount)|Obtiene el número de elementos de esta matriz.|  
|[CObArray::GetData](#getdata)|Permite el acceso a los elementos de la matriz. Puede ser **NULL**.|  
|[CObArray::GetSize](#getsize)|Obtiene el número de elementos de esta matriz.|  
|[CObArray::GetUpperBound](#getupperbound)|Devuelve el índice válido de mayor tamaño.|  
|[CObArray::InsertAt](#insertat)|Inserta un elemento (o todos los elementos de otra matriz) en un índice especificado.|  
|[CObArray::IsEmpty](#isempty)|Determina si la matriz está vacía.|  
|[CObArray::RemoveAll](#removeall)|Quita todos los elementos de esta matriz.|  
|[CObArray::RemoveAt](#removeat)|Quita un elemento en un índice específico.|  
|[CObArray::SetAt](#setat)|Establece el valor de un índice dado; la matriz no puede aumentar de tamaño.|  
|[CObArray::SetAtGrow](#setatgrow)|Establece el valor de un índice dado; aumenta el tamaño de la matriz si es necesario.|  
|[CObArray::SetSize](#setsize)|Establece el número de elementos que contendrá esta matriz.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[[] CObArray::operator](#operator_at)|Establece u obtiene el elemento en el índice especificado.|  
  
## <a name="remarks"></a>Comentarios  
 Estas matrices de objetos son similares a las matrices de C, pero dinámicamente pueden reducir y crecer según sea necesarios.  
  
 Los índices de matriz siempre se inician en la posición 0. Puede decidir si desea corregir el límite superior o permitir que la matriz expandir cuando se agregan elementos más allá del límite actual. Memoria se asigna de forma contigua al límite superior, aunque algunos elementos son nulos.  
  
 En Win32, el tamaño de una `CObArray` objeto se limita únicamente a la memoria disponible.  
  
 Al igual que con una matriz de C, la hora de acceso de un `CObArray` elemento indizado es constante y es independiente del tamaño de matriz.  
  
 `CObArray` incorpora la macro `IMPLEMENT_SERIAL` para admitir la serialización y el volcado de sus elementos. Si una matriz de `CObject` punteros se almacena en un archivo, con el operador de inserción sobrecargado o con el `Serialize` miembro funcione, cada uno de ellos `CObject` a su vez, se, serializa el elemento junto con su índice de matriz.  
  
 Si se necesita un volcado de persona `CObject` elementos de una matriz, se debe establecer la profundidad de la `CDumpContext` objeto a 1 o mayor.  
  
 Cuando un `CObArray` se elimina el objeto, o cuando se quitan sus elementos, solo la `CObject` se quitan los punteros, no los objetos que hacen referencia.  
  
> [!NOTE]
>  Antes de usar una matriz, use `SetSize` para establecer su tamaño y asignarle memoria. Si no usa `SetSize`, al agregar elementos a la matriz, esta se reasigna y se copia con frecuencia. La reasignación y copia frecuentes son ineficaces y pueden fragmentar la memoria.  
  
 Derivación de la clase de matriz es similar a la derivación de la lista. Para obtener detalles sobre la derivación de una clase especial list, vea el artículo [colecciones](../../mfc/collections.md).  
  
> [!NOTE]
>  Debe utilizar el `IMPLEMENT_SERIAL` macro en la implementación de la clase derivada si va a serializar la matriz.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CObArray`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcoll.h  
  
##  <a name="add"></a>CObArray::Add  
 Agrega un nuevo elemento al final de una matriz, aumentando la matriz en 1.  
  
```  
INT_PTR Add(CObject* newElement);
```  
  
### <a name="parameters"></a>Parámetros  
 `newElement`  
 El `CObject` puntero va a agregar a esta matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del elemento agregado.  
  
### <a name="remarks"></a>Comentarios  
 Si [SetSize](#setsize) se ha utilizado con un `nGrowBy` puede asignarse valor mayor que 1, memoria adicional. Sin embargo, el límite superior aumentarán en 1 solo.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObArray::Add`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Agregar INT_PTR (BYTE** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Agregar INT_PTR (DWORD** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR Add( void\*** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Agregar INT_PTR (LPCTSTR** `newElement` **); throw (CMemoryException\* );**<br /><br /> **INT_PTR Add(const CString&** `newElement` **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Agregar INT_PTR (UINT** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Agregar INT_PTR (WORD** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
  
### <a name="example"></a>Ejemplo  
  Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections #75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]  
  
 Los resultados de este programa son los siguientes:  
  
 `Add example: A CObArray with 2 elements`  
  
 `[0] = a CAge at $442A 21`  
  
 `[1] = a CAge at $4468 40`  
  
##  <a name="append"></a>CObArray::Append  
 Llame a esta función miembro para agregar el contenido de otra matriz hasta el final de la matriz.  
  
```  
INT_PTR Append(const CObArray& src);
```  
  
### <a name="parameters"></a>Parámetros  
 *src*  
 Origen de los elementos que se debe anexar a la matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del primer elemento anexado.  
  
### <a name="remarks"></a>Comentarios  
 Las matrices deben ser del mismo tipo.  
  
 Si es necesario, **anexión** puede asignar memoria adicional para dar cabida a los elementos que se anexa a la matriz.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObArray::Append`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Anexar INT_PTR (const CByteArray siguiente** *src* **);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Anexar INT_PTR (const CDWordArray siguiente** *src* **);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Anexar INT_PTR (const CPtrArray siguiente** *src* **);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Anexar INT_PTR (const CStringArray siguiente** *src* **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Anexar INT_PTR (const CUIntArray siguiente** *src* **);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Anexar INT_PTR (const CWordArray siguiente** *src* **);**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections #76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]  
  
##  <a name="copy"></a>CObArray::Copy  
 Llame a esta función miembro para sobrescribir los elementos de la matriz con los elementos de otra matriz del mismo tipo.  
  
```  
void Copy(const CObArray& src);
```  
  
### <a name="parameters"></a>Parámetros  
 *src*  
 Origen de los elementos que se copian a la matriz.  
  
### <a name="remarks"></a>Comentarios  
 **Copia** no libera memoria; sin embargo, si es necesario, **copia** puede asignar memoria adicional para dar cabida a los elementos que se copian en la matriz.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObArray::Copy`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**anular copia (const CByteArray siguiente** *src* **);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**anular copia (const CDWordArray siguiente** *src* **);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**anular copia (const CPtrArray siguiente** *src* **);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**anular copia (const CStringArray siguiente** *src* **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**anular copia (const CUIntArray siguiente** *src* **);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**anular copia (const CWordArray siguiente** *src* **);**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections #77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]  
  
##  <a name="cobarray"></a>CObArray::CObArray  
 Construye un vacío `CObject` matriz de puntero.  
  
```  
CObArray();
```  
  
### <a name="remarks"></a>Comentarios  
 La matriz aumenta de tamaño un elemento a la vez.  
  
 La tabla siguiente muestran otros constructores que son similares a `CObArray::CObArray`.  
  
|Clase|Constructor|  
|-----------|-----------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**CByteArray ();**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**CDWordArray ();**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**CPtrArray ();**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CStringArray ();**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**CUIntArray ();**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**CWordArray ();**|  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCollections #78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]  
  
##  <a name="elementat"></a>CObArray::ElementAt  
 Devuelve una referencia temporal al puntero del elemento dentro de la matriz.  
  
```  
CObject*& ElementAt(INT_PTR nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Un índice de entero que es mayor o igual que 0 y menor o igual que el valor devuelto por `GetUpperBound`.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a un `CObject` puntero.  
  
### <a name="remarks"></a>Comentarios  
 Se utiliza para implementar el operador de asignación de la izquierda para matrices. Tenga en cuenta que se trata de una función avanzada que debe usarse solo para implementar operadores de matriz especiales.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObArray::ElementAt`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE siguiente ElementAt (INT_PTR** `nIndex` **);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD siguiente ElementAt (INT_PTR** `nIndex` **);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\*siguiente ElementAt (INT_PTR** `nIndex` **);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString siguiente ElementAt (INT_PTR** `nIndex` **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT siguiente ElementAt (INT_PTR** `nIndex` **);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**PALABRA siguiente ElementAt (INT_PTR** `nIndex` **);**|  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CObArray::GetSize](#getsize).  
  
##  <a name="freeextra"></a>CObArray::FreeExtra  
 Libera la memoria adicional que se asignó mientras se ha aumentado la matriz.  
  
```  
void FreeExtra();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función no influye en el tamaño o el límite superior de la matriz.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObArray::FreeExtra`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void FreeExtra ();**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void FreeExtra ();**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void FreeExtra ();**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void FreeExtra ();**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void FreeExtra ();**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void FreeExtra ();**|  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CObArray::GetData](#getdata).  
  
##  <a name="getat"></a>CObArray::GetAt  
 Devuelve el elemento de matriz en el índice especificado.  
  
```  
CObject* GetAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Un índice de entero que es mayor o igual que 0 y menor o igual que el valor devuelto por `GetUpperBound`.  
  
### <a name="return-value"></a>Valor devuelto  
 El `CObject` elemento de puntero actualmente en este índice.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Pasar un valor negativo o un valor mayor que el valor devuelto por `GetUpperBound` dará como resultado un error de aserción.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObArray::GetAt`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTES GetAt (INT_PTR** `nIndex` **) const;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**GetAt DWORD (INT_PTR** `nIndex` **) const;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\* GetAt (INT_PTR** `nIndex` **) const;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString GetAt (INT_PTR** `nIndex` **) const;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**GetAt UINT (INT_PTR** `nIndex` **) const;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD GetAt (INT_PTR** `nIndex` **) const;**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections #79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]  
  
##  <a name="getcount"></a>CObArray::GetCount  
 Devuelve el número de elementos de matriz.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de elementos de la matriz.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para recuperar el número de elementos de la matriz. Dado que los índices son de base cero, el tamaño es mayor que el índice más grande de 1.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObArray::GetCount`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetCount () const;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetCount () const;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetCount () const;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetCount () const;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetCount () const;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetCount () const;**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections #80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]  
  
##  <a name="getdata"></a>CObArray::GetData  
 Utilice esta función miembro para tener acceso directo a los elementos de la matriz.  
  
```  
const CObject** GetData() const;  
  
CObject** GetData();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la matriz de `CObject` punteros.  
  
### <a name="remarks"></a>Comentarios  
 Si no hay elementos disponibles, `GetData` devuelve un valor null.  
  
 Aunque el acceso directo a los elementos de una matriz puede ayudarle a trabajar más rápidamente, tenga cuidado al llamar a `GetData`; los errores que se realiza directamente afectan a los elementos de la matriz.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObArray::GetData`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTES const\* GetData () const; BYTES\* GetData ();**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD const\* GetData () const; DWORD\* GetData ();**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Const void\* \* () GetData const; void\* \* GetData ();**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**const CString\* GetData () const; CString\* GetData ();**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT const\* GetData () const; UINT\* GetData ();**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD const\* GetData () const; WORD\* GetData ();**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections #81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]  
  
##  <a name="getsize"></a>CObArray::GetSize  
 Devuelve el tamaño de la matriz.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="remarks"></a>Comentarios  
 Puesto que los índices son de base cero, el tamaño es mayor que el índice más grande de 1.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObArray::GetSize`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetSize () const;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetSize () const;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetSize () const;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetSize () const;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetSize () const;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetSize () const;**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections #82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]  
  
##  <a name="getupperbound"></a>CObArray::GetUpperBound  
 Devuelve el límite superior actual de esta matriz.  
  
```  
INT_PTR GetUpperBound() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El índice de límite superior (basado en cero).  
  
### <a name="remarks"></a>Comentarios  
 Dado que los índices de matriz son de base cero, esta función devuelve un valor de 1 menor que `GetSize`.  
  
 La condición **() GetUpperBound** = -1 indica que la matriz no contiene elementos.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObArray::GetUpperBound`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetUpperBound () const;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetUpperBound () const;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetUpperBound () const;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetUpperBound () const;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetUpperBound () const;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetUpperBound () const;**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections número 83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]  
  
##  <a name="insertat"></a>CObArray::InsertAt  
 Inserta un elemento (o todos los elementos de otra matriz) en un índice especificado.  
  
```  
void InsertAt(
    INT_PTR nIndex,  
    CObject* newElement,  
    INT_PTR nCount = 1);

 
void InsertAt(
    INT_PTR nStartIndex,  
    CObArray* pNewArray);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Un índice de entero que puede ser mayor que el valor devuelto por `GetUpperBound`.  
  
 `newElement`  
 El `CObject` puntero que se colocarán en esta matriz. A `newElement` del valor **NULL** está permitido.  
  
 `nCount`  
 El número de veces que este elemento debe estar insertado (el valor predeterminado es 1).  
  
 `nStartIndex`  
 Un índice de entero que puede ser mayor que el valor devuelto por `GetUpperBound`.  
  
 `pNewArray`  
 Otra matriz que contiene elementos que se va a agregar a esta matriz.  
  
### <a name="remarks"></a>Comentarios  
 La primera versión de `InsertAt` inserta un elemento (o varias copias de un elemento) en el índice especificado en una matriz. En el proceso, desplaza (al incrementar el índice) el elemento existente en este índice y lo pasa todos los elementos por encima de él.  
  
 La segunda versión inserta todos los elementos de otro `CObArray` colección, comenzando por la `nStartIndex` posición.  
  
 El `SetAt` función, en cambio, reemplaza un elemento de la matriz especificada y desplazar los elementos.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObArray::InsertAt`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, BYTE** `newElement` **, int** `nCount` **= 1 );**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CByteArray\*** `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, DWORD** `newElement` **, int** `nCount` **= 1 );**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CDWordArray\*** `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, void\*** `newElement` **, int** `nCount` **= 1 );**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CPtrArray\*** `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, LPCTSTR** `newElement` **, int** `nCount` **= 1 );**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CStringArray\*** `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, UINT** `newElement` **, int** `nCount` **= 1 );**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CUIntArray\*** `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, WORD** `newElement` **, int** `nCount` **= 1 );**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CWordArray\*** `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|  
  
### <a name="example"></a>Ejemplo  
  Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections #84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]  
  
 Los resultados de este programa son los siguientes:  
  
 `InsertAt example: A CObArray with 3 elements`  
  
 `[0] = a CAge at $45C8 21`  
  
 `[1] = a CAge at $4646 30`  
  
 `[2] = a CAge at $4606 40`  
  
##  <a name="isempty"></a>CObArray::IsEmpty  
 Determina si la matriz está vacía.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la matriz está vacía; en caso contrario es 0.  
  
##  <a name="operator_at"></a>[] CObArray::operator  
 Estos operadores de subíndice son un sustituto adecuado para la `SetAt` y `GetAt` funciones.  
  
```  
CObject*& operator[](int_ptr nindex);  
CObject* operator[](int_ptr nindex) const;  
```  
  
### <a name="remarks"></a>Comentarios  
 El primer operador llama para las matrices que no son **const**, puede utilizarse en el (valor r) de la derecha o la izquierda (valor l) de una instrucción de asignación. El segundo, se llama para **const** arreglos de discos, puede utilizarse solo a la derecha.  
  
 La versión de la biblioteca de depuración valida si el subíndice (ya sea en el lado izquierdo o derecho de una instrucción de asignación) está fuera de límites.  
  
 La tabla siguiente muestran otros operadores que son similares a **[] CObArray::operator**.  
  
|Clase|Operador|  
|-----------|--------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE siguiente operador [] (int_ptr** `nindex` **\);**<br /><br /> **Operador BYTE [] (int_ptr** `nindex` **\) const;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD siguiente operador [] (int_ptr** `nindex` **\);**<br /><br /> **Operador [DWORD] (int_ptr** `nindex` **\) const;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\*& operator [](int_ptr** `nindex` **\);**<br /><br /> **void\* operator [] (int_ptr** `nindex` **\) const;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString siguiente operador [] (int_ptr** `nindex` **\);**<br /><br /> **CString operator [] (int_ptr** `nindex` **\) const;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT siguiente operador [] (int_ptr** `nindex` **\);**<br /><br /> **UINT operator [] (int_ptr** `nindex` **\) const;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**PALABRA siguiente operador [] (int_ptr** `nindex` **\);**<br /><br /> **WORD operator [] (int_ptr** `nindex` **\) const;**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections #88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]  
  
##  <a name="removeall"></a>CObArray::RemoveAll  
 Quita todos los punteros de esta matriz, pero no se eliminan realmente el `CObject` objetos.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Comentarios  
 Si la matriz está vacía, la función sigue funcionando.  
  
 El `RemoveAll` función libera toda la memoria utilizada para el almacenamiento de puntero.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObArray::RemoveAll`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAll ();**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAll ();**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAll ();**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAll ();**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAll ();**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAll ();**|  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections #85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]  
  
##  <a name="removeat"></a>CObArray::RemoveAt  
 Quita uno o más elementos, empezando por un índice especificado en una matriz.  
  
```  
void RemoveAt(
    INT_PTR nIndex,  
    INT_PTR nCount = 1);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Un índice de entero que es mayor o igual que 0 y menor o igual que el valor devuelto por `GetUpperBound`.  
  
 `nCount`  
 Número de elementos que se va a quitar.  
  
### <a name="remarks"></a>Comentarios  
 En el proceso, desplaza hacia abajo todos los elementos por encima de los elementos quitados. Se reduce la esquina superior límite de la matriz, pero no libera memoria.  
  
 Si intenta quitar más elementos de los que se encuentran en la matriz por encima del punto de eliminación, se valida la versión de la biblioteca de depuración.  
  
 El `RemoveAt` función quita el `CObject` puntero de la matriz, pero no elimina el objeto propiamente dicho.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObArray::RemoveAt`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** *nCount* **= 1);**|  
  
### <a name="example"></a>Ejemplo  
  Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections #112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]  
  
 Los resultados de este programa son los siguientes:  
  
 `RemoveAt example: A CObArray with 1 elements`  
  
 `[0] = a CAge at $4606 40`  
  
##  <a name="setat"></a>CObArray::SetAt  
 Establece el elemento de matriz en el índice especificado.  
  
```  
void SetAt(
    INT_PTR nIndex,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Un índice de entero que es mayor o igual que 0 y menor o igual que el valor devuelto por `GetUpperBound`.  
  
 `newElement`  
 Puntero de objeto que se van a insertar en esta matriz. A **NULL** se permite el valor.  
  
### <a name="remarks"></a>Comentarios  
 `SetAt`no se hará que la matriz crezca. Use `SetAtGrow` si desea que la matriz para crecer automáticamente.  
  
 Debe asegurarse de que el valor de índice representa una posición válida en la matriz. Si no fuera de los límites, se valida la versión de la biblioteca de depuración.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObArray::SetAt`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAt( INT_PTR** `nIndex` **, BYTE** `newElement` **);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, DWORD** `newElement` **);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, void\*** `newElement` **);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, UINT** `newElement` **);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, WORD** `newElement` **);**|  
  
### <a name="example"></a>Ejemplo  
  Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections #86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]  
  
 Los resultados de este programa son los siguientes:  
  
 `SetAt example: A CObArray with 2 elements`  
  
 `[0] = a CAge at $47E0 30`  
  
 `[1] = a CAge at $47A0 40`  
  
##  <a name="setatgrow"></a>CObArray::SetAtGrow  
 Establece el elemento de matriz en el índice especificado.  
  
```  
void SetAtGrow(
    INT_PTR nIndex,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Un índice de entero que es mayor o igual que 0.  
  
 `newElement`  
 Puntero de objeto que se va a agregar a esta matriz. A **NULL** se permite el valor.  
  
### <a name="remarks"></a>Comentarios  
 La matriz crece automáticamente si es necesario (es decir, el límite superior se ajusta para alojar el nuevo elemento).  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObArray::SetAtGrow`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, BYTE** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, DWORD** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, void\*** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, UINT** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, WORD** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
  
### <a name="example"></a>Ejemplo  
  Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los ejemplos de la colección.  
  
 [!code-cpp[NVC_MFCCollections #87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]  
  
 Los resultados de este programa son los siguientes:  
  
 `SetAtGrow example: A CObArray with 4 elements`  
  
 `[0] = a CAge at $47C0 21`  
  
 `[1] = a CAge at $4800 40`  
  
 `[2] = NULL`  
  
 `[3] = a CAge at $4840 65`  
  
##  <a name="setsize"></a>CObArray::SetSize  
 Establece el tamaño de una matriz vacía o existente; asigna memoria si es necesario.  
  
```  
void SetSize(
    INT_PTR nNewSize,  
    INT_PTR nGrowBy = -1);
```  
  
### <a name="parameters"></a>Parámetros  
 `nNewSize`  
 El nuevo tamaño de la matriz (número de elementos). Debe ser mayor o igual que 0.  
  
 `nGrowBy`  
 El número mínimo de ranuras de elemento para asignar si es necesario un aumento de tamaño.  
  
### <a name="remarks"></a>Comentarios  
 Si el nuevo tamaño es menor que el tamaño anterior, la matriz se trunca y se libera toda la memoria sin usar. Para mejorar la eficacia, llame a `SetSize` para establecer el tamaño de la matriz antes de usarlo. Esto evita la necesidad de reasignar y copiar cada vez que se agrega un elemento de la matriz.  
  
 El `nGrowBy` parámetro afecta a la asignación de memoria interna mientras está aumentando la matriz. Su uso nunca afecta al tamaño de matriz devuelto por `GetSize` y `GetUpperBound`.  
  
 Si ha aumentado el tamaño de la matriz, todos los recién asignada **CObject \*** punteros se establecen en NULL.  
  
 En la tabla siguiente se muestra otro miembro funciones que son similares a `CObArray::SetSize`.  
  
|Clase|Función miembro|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1 );**<br /><br /> **throw (CMemoryException\* );**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1 );**<br /><br /> **throw (CMemoryException\* );**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1 );**<br /><br /> **throw (CMemoryException\* );**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1 );**<br /><br /> **throw (CMemoryException\* );**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1 );**<br /><br /> **throw (CMemoryException\* );**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1 );**<br /><br /> **throw (CMemoryException\* );**|  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CObArray::GetData](#getdata).  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clase CStringArray](../../mfc/reference/cstringarray-class.md)   
 [Clase CPtrArray](../../mfc/reference/cptrarray-class.md)   
 [CByteArray (clase)](../../mfc/reference/cbytearray-class.md)   
 [Clase CWordArray](../../mfc/reference/cwordarray-class.md)   
 [CDWordArray (clase)](../../mfc/reference/cdwordarray-class.md)

