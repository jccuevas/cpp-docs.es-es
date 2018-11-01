---
title: CShellManager (clase)
ms.date: 11/04/2016
f1_keywords:
- CShellManager
- AFXSHELLMANAGER/CShellManager
- AFXSHELLMANAGER/CShellManager::CShellManager
- AFXSHELLMANAGER/CShellManager::BrowseForFolder
- AFXSHELLMANAGER/CShellManager::ConcatenateItem
- AFXSHELLMANAGER/CShellManager::CopyItem
- AFXSHELLMANAGER/CShellManager::CreateItem
- AFXSHELLMANAGER/CShellManager::FreeItem
- AFXSHELLMANAGER/CShellManager::GetItemCount
- AFXSHELLMANAGER/CShellManager::GetItemSize
- AFXSHELLMANAGER/CShellManager::GetNextItem
- AFXSHELLMANAGER/CShellManager::GetParentItem
- AFXSHELLMANAGER/CShellManager::ItemFromPath
helpviewer_keywords:
- CShellManager [MFC], CShellManager
- CShellManager [MFC], BrowseForFolder
- CShellManager [MFC], ConcatenateItem
- CShellManager [MFC], CopyItem
- CShellManager [MFC], CreateItem
- CShellManager [MFC], FreeItem
- CShellManager [MFC], GetItemCount
- CShellManager [MFC], GetItemSize
- CShellManager [MFC], GetNextItem
- CShellManager [MFC], GetParentItem
- CShellManager [MFC], ItemFromPath
ms.assetid: f15c4c1a-6fae-487d-9913-9b7369b33da0
ms.openlocfilehash: 428f64dadb91887c4d076693e5dc939b6aff7680
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571241"
---
# <a name="cshellmanager-class"></a>CShellManager (clase)

Implementa varios métodos que permiten trabajar con punteros en listas de identificadores (PIDL).

## <a name="syntax"></a>Sintaxis

```
class CShellManager : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CShellManager::CShellManager](#cshellmanager)|Construye un objeto `CShellManager`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CShellManager::BrowseForFolder](#browseforfolder)|Muestra un cuadro de diálogo que permite al usuario seleccionar una carpeta de shell.|
|[CShellManager::ConcatenateItem](#concatenateitem)|Concatena dos PIDLs.|
|[CShellManager::CopyItem](#copyitem)|Crea un nuevo PIDL y copia el PIDL proporcionado en él.|
|[CShellManager::CreateItem](#createitem)|Crea un nuevo PIDL del tamaño especificado.|
|[CShellManager::FreeItem](#freeitem)|Elimina el PIDL proporcionado.|
|[CShellManager::GetItemCount](#getitemcount)|Devuelve el número de elementos en el PIDL proporcionado.|
|[CShellManager::GetItemSize](#getitemsize)|Devuelve el tamaño de la PIDL proporcionado.|
|[CShellManager::GetNextItem](#getnextitem)|Devuelve el elemento siguiente de la PIDL.|
|[CShellManager::GetParentItem](#getparentitem)|Recupera el elemento primario del elemento proporcionado.|
|[CShellManager::ItemFromPath](#itemfrompath)|Recupera el PIDL para el elemento identificado por la ruta de acceso proporcionada.|

## <a name="remarks"></a>Comentarios

Los métodos de la `CShellManager` todas homónimo PIDLs de clase. Un PIDL es un identificador único para un objeto del shell.

No debería crear un `CShellManager` objeto manualmente. Se creará automáticamente el marco de trabajo de la aplicación. Sin embargo, debe llamar a [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) durante el proceso de inicialización de la aplicación. Para obtener un puntero para el Administrador de shell para la aplicación, llame a [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CShellManager](../../mfc/reference/cshellmanager-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxshellmanager.h

##  <a name="browseforfolder"></a>  CShellManager::BrowseForFolder

Muestra un cuadro de diálogo que permite al usuario seleccionar una carpeta de shell.

```
BOOL BrowseForFolder(
    CString& strOutFolder,
    CWnd* pWndParent = NULL,
    LPCTSTR lplszInitialFolder = NULL,
    LPCTSTR lpszTitle = NULL,
    UINT ulFlags = BIF_RETURNONLYFSDIRS,
    LPINT piFolderImage = NULL);
```

### <a name="parameters"></a>Parámetros

*strOutFolder*<br/>
[out] La cadena utilizada por el método para almacenar la ruta de acceso de la carpeta seleccionada.

*pWndParent*<br/>
[in] Un puntero a la ventana primaria.

*lplszInitialFolder*<br/>
[in] Una cadena que contiene la carpeta que está seleccionada de forma predeterminada cuando se muestra el cuadro de diálogo.

*lpszTitle*<br/>
[in] El título del cuadro de diálogo.

*ulFlags*<br/>
[in] Marcas que especifican las opciones del cuadro de diálogo. Consulte [BROWSEINFO](/windows/desktop/api/shlobj_core/ns-shlobj_core-_browseinfoa) la descripción detallada.

*piFolderImage*<br/>
[out] Un puntero al valor entero que el método escribe el índice de imagen de la carpeta seleccionada.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario selecciona una carpeta en el cuadro de diálogo; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Cuando se llama a este método, la aplicación crea y muestra un cuadro de diálogo que permite al usuario seleccionar una carpeta. El método va a escribir la ruta de acceso de la carpeta en la *strOutFolder* parámetro.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo recuperar una referencia a un `CShellManager` objeto utilizando el `CWinAppEx::GetShellManager` método y cómo usar el `BrowseForFolder` método. Este fragmento de código forma parte de la [ejemplo Explorer](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]

##  <a name="concatenateitem"></a>  CShellManager::ConcatenateItem

Crea una nueva lista que contiene dos PIDLs.

```
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,
    LPCITEMIDLIST pidl2);
```

### <a name="parameters"></a>Parámetros

*pidl1*<br/>
[in] El primer elemento.

*pidl2*<br/>
[in] El segundo elemento.

### <a name="return-value"></a>Valor devuelto

Un puntero a la nueva lista de elementos si la función se realiza correctamente, en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

Este método crea un nuevo [ITEMIDLIST](/windows/desktop/api/shtypes/ns-shtypes-_itemidlist) suficientemente grande como para contener ambos *pidl1* y *pidl2*. A continuación, copia *pidl1* y *pidl2* a la nueva lista.

##  <a name="copyitem"></a>  CShellManager::CopyItem

Copia una lista de elementos.

```
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```

### <a name="parameters"></a>Parámetros

*pidlSource*<br/>
[in] La lista de elementos original.

### <a name="return-value"></a>Valor devuelto

Un puntero a la lista de los elementos recién creado si se realiza correctamente; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

La lista de los elementos recién creado tiene el mismo tamaño que la lista de elementos de origen.

##  <a name="createitem"></a>  CShellManager::CreateItem

Crea un nuevo PIDL.

```
LPITEMIDLIST CreateItem(UINT cbSize);
```

### <a name="parameters"></a>Parámetros

*cbSize*<br/>
[in] El tamaño de la lista de elementos.

### <a name="return-value"></a>Valor devuelto

Un puntero a la lista de elementos creados si se realiza correctamente; en caso contrario, es NULL.

##  <a name="cshellmanager"></a>  CShellManager::CShellManager

Construye un objeto `CShellManager`.

```
CShellManager();
```

### <a name="remarks"></a>Comentarios

En la mayoría de los casos, no es necesario crear un `CShellManager` directamente. De forma predeterminada, el marco de trabajo crea uno automáticamente. Para obtener un puntero a la `CShellManager`, llame a [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager). Si creas un `CShellManager` manualmente, debe inicializar con el método [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager).

##  <a name="freeitem"></a>  CShellManager::FreeItem

Elimina una lista de elementos.

```
void FreeItem(LPITEMIDLIST pidl);
```

### <a name="parameters"></a>Parámetros

*PIDL*<br/>
[in] Para eliminar una lista de elementos.

##  <a name="getitemcount"></a>  CShellManager::GetItemCount

Devuelve el número de elementos en una lista de elementos.

```
UINT GetItemCount(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parámetros

*PIDL*<br/>
[in] Un puntero a una lista de elementos.

### <a name="return-value"></a>Valor devuelto

El número de elementos en la lista de elementos.

##  <a name="getitemsize"></a>  CShellManager::GetItemSize

Devuelve el tamaño de una lista de elementos.

```
UINT GetItemSize(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parámetros

*PIDL*<br/>
[in] Un puntero a una lista de elementos.

### <a name="return-value"></a>Valor devuelto

El tamaño de la lista de elementos.

##  <a name="getnextitem"></a>  CShellManager::GetNextItem

Recupera el siguiente elemento de un puntero a una lista de identificador de elemento (PIDL).

```
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parámetros

*PIDL*<br/>
[in] La lista de elementos que se va a iterar.

### <a name="return-value"></a>Valor devuelto

Un puntero al elemento siguiente en la lista.

### <a name="remarks"></a>Comentarios

Si no hay ningún elemento más en la lista, este método devuelve NULL.

##  <a name="getparentitem"></a>  CShellManager::GetParentItem

Recupera al elemento primario de un puntero a una lista de identificador de elemento (PIDL).

```
int GetParentItem(
    LPCITEMIDLIST lpidl,
    LPITEMIDLIST& lpidlParent);
```

### <a name="parameters"></a>Parámetros

*lpidl*<br/>
[in] Un PIDL cuyo elemento primario se va a recuperar.

*lpidlParent*<br/>
[out] Una referencia a un PIDL donde el método almacenará el resultado.

### <a name="return-value"></a>Valor devuelto

El nivel del elemento primario PIDL.

### <a name="remarks"></a>Comentarios

Es el nivel de un PIDL en relación con el escritorio. El escritorio PIDL se considera que tiene un nivel de 0.

##  <a name="itemfrompath"></a>  CShellManager::ItemFromPath

Recupera el puntero a una lista de identificador de elemento (PIDL) desde el elemento identificado por una ruta de acceso de cadena.

```
HRESULT ItemFromPath(
    LPCTSTR lpszPath,
    LPITEMIDLIST& pidl);
```

### <a name="parameters"></a>Parámetros

*lpszPath*<br/>
[in] Una cadena que especifica la ruta de acceso para el elemento.

*PIDL*<br/>
[out] Una referencia a un PIDL. El método usa este PIDL para almacenar el puntero a su valor devuelto.

### <a name="return-value"></a>Valor devuelto

Devuelve NOERROR si se realiza correctamente; un valor de error definido por OLE.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
