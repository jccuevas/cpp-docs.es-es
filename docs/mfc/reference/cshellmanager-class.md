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
ms.openlocfilehash: cc8aa9216fd0d4dcc169830fb745134ceb5c65fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318410"
---
# <a name="cshellmanager-class"></a>CShellManager (clase)

Implementa varios métodos que permiten trabajar con punteros en listas de identificadores (PIDL).

## <a name="syntax"></a>Sintaxis

```
class CShellManager : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CShellManager::CShellManager](#cshellmanager)|Construye un objeto `CShellManager`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CShellManager::BrowseForFolder](#browseforfolder)|Muestra un cuadro de diálogo que permite al usuario seleccionar una carpeta de shell.|
|[CShellManager::ConcatenateItem](#concatenateitem)|Concatena dos PIDL.|
|[CShellManager::CopyItem](#copyitem)|Crea un nuevo PIDL y copia el PIDL proporcionado en él.|
|[CShellManager::CreateItem](#createitem)|Crea un nuevo PIDL del tamaño especificado.|
|[CShellManager::FreeItem](#freeitem)|Elimina el PIDL suministrado.|
|[CShellManager::GetItemCount](#getitemcount)|Devuelve el número de elementos del PIDL proporcionado.|
|[CShellManager::GetItemSize](#getitemsize)|Devuelve el tamaño del PIDL proporcionado.|
|[CShellManager::GetNextItem](#getnextitem)|Devuelve el siguiente elemento de la PIDL.|
|[CShellManager::GetParentItem](#getparentitem)|Recupera el elemento primario del elemento proporcionado.|
|[CShellManager::ItemFromPath](#itemfrompath)|Recupera el PIDL para el elemento identificado por la ruta de acceso proporcionada.|

## <a name="remarks"></a>Observaciones

Todos los `CShellManager` métodos de la clase tratan con PIDLs. Un PIDL es un identificador único para un objeto de shell.

No debe crear `CShellManager` un objeto manualmente. Se creará automáticamente por el marco de la aplicación. Sin embargo, debe llamar a [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) durante el proceso de inicialización de la aplicación. Para obtener un puntero al administrador de shell de la aplicación, llame a [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CShellManager](../../mfc/reference/cshellmanager-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxshellmanager.h

## <a name="cshellmanagerbrowseforfolder"></a><a name="browseforfolder"></a>CShellManager::BrowseForFolder

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
[fuera] Cadena utilizada por el método para almacenar la ruta de acceso de la carpeta seleccionada.

*pWndParent*<br/>
[en] Un puntero a la ventana primaria.

*lplszInitialFolder*<br/>
[en] Cadena que contiene la carpeta seleccionada de forma predeterminada cuando se muestra el cuadro de diálogo.

*lpszTitle*<br/>
[en] El título del cuadro de diálogo.

*ulFlags*<br/>
[en] Indicadores que especifican opciones para el cuadro de diálogo. Consulte [BROWSEINFO](/windows/win32/api/shlobj_core/ns-shlobj_core-browseinfow) para obtener la descripción detallada.

*piFolderImage*<br/>
[fuera] Puntero al valor entero donde el método escribe el índice de imagen de la carpeta seleccionada.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario selecciona una carpeta en el cuadro de diálogo; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Cuando se llama a este método, la aplicación crea y muestra un cuadro de diálogo que permite al usuario seleccionar una carpeta. El método escribirá la ruta de acceso de la carpeta en el parámetro *strOutFolder.*

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CShellManager` cómo recuperar `CWinAppEx::GetShellManager` una referencia a `BrowseForFolder` un objeto mediante el método y cómo utilizar el método. Este fragmento de código forma parte del [ejemplo Explorer](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]

## <a name="cshellmanagerconcatenateitem"></a><a name="concatenateitem"></a>CShellManager::ConcatenateItem

Crea una nueva lista que contiene dos PIDL.

```
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,
    LPCITEMIDLIST pidl2);
```

### <a name="parameters"></a>Parámetros

*pidl1*<br/>
[en] El primer elemento.

*pidl2*<br/>
[en] El segundo elemento.

### <a name="return-value"></a>Valor devuelto

Un puntero a la nueva lista de elementos si la función se realiza correctamente, de lo contrario NULL.

### <a name="remarks"></a>Observaciones

Este método crea un nuevo [ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist) lo suficientemente grande como para contener *pidl1* y *pidl2*. A continuación, copia *pidl1* y *pidl2* en la nueva lista.

## <a name="cshellmanagercopyitem"></a><a name="copyitem"></a>CShellManager::CopyItem

Copia una lista de elementos.

```
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```

### <a name="parameters"></a>Parámetros

*pidlSource*<br/>
[en] La lista de artículos original.

### <a name="return-value"></a>Valor devuelto

Un puntero a la lista de elementos recién creada si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

La lista de elementos recién creada tiene el mismo tamaño que la lista de elementos de origen.

## <a name="cshellmanagercreateitem"></a><a name="createitem"></a>CShellManager::CreateItem

Crea un nuevo PIDL.

```
LPITEMIDLIST CreateItem(UINT cbSize);
```

### <a name="parameters"></a>Parámetros

*cbSize*<br/>
[en] El tamaño de la lista de elementos.

### <a name="return-value"></a>Valor devuelto

Un puntero a la lista de elementos creados si se realiza correctamente; NULL.

## <a name="cshellmanagercshellmanager"></a><a name="cshellmanager"></a>CShellManager::CShellManager

Construye un objeto `CShellManager`.

```
CShellManager();
```

### <a name="remarks"></a>Observaciones

En la mayoría de los casos, no es necesario crear un `CShellManager` directamente. De forma predeterminada, el marco de trabajo crea uno para usted. Para obtener un `CShellManager`puntero a la , llame a [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager). Si crea un `CShellManager` manualmente, debe inicializarlo con el método [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager).

## <a name="cshellmanagerfreeitem"></a><a name="freeitem"></a>CShellManager::FreeItem

Elimina una lista de elementos.

```
void FreeItem(LPITEMIDLIST pidl);
```

### <a name="parameters"></a>Parámetros

*pidl*<br/>
[en] Una lista de elementos para eliminar.

## <a name="cshellmanagergetitemcount"></a><a name="getitemcount"></a>CShellManager::GetItemCount

Devuelve el número de elementos de una lista de elementos.

```
UINT GetItemCount(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parámetros

*pidl*<br/>
[en] Un puntero a una lista de elementos.

### <a name="return-value"></a>Valor devuelto

El número de elementos de la lista de artículos.

## <a name="cshellmanagergetitemsize"></a><a name="getitemsize"></a>CShellManager::GetItemSize

Devuelve el tamaño de una lista de elementos.

```
UINT GetItemSize(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parámetros

*pidl*<br/>
[en] Un puntero a una lista de elementos.

### <a name="return-value"></a>Valor devuelto

El tamaño de la lista de elementos.

## <a name="cshellmanagergetnextitem"></a><a name="getnextitem"></a>CShellManager::GetNextItem

Recupera el siguiente elemento de un puntero a una lista de identificadores de elemento (PIDL).

```
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parámetros

*pidl*<br/>
[en] La lista de elementos que se va a iterar.

### <a name="return-value"></a>Valor devuelto

Un puntero al siguiente elemento de la lista.

### <a name="remarks"></a>Observaciones

Si no hay más elementos en la lista, este método devuelve NULL.

## <a name="cshellmanagergetparentitem"></a><a name="getparentitem"></a>CShellManager::GetParentItem

Recupera el elemento primario de un puntero a una lista de identificadores de elemento (PIDL).

```
int GetParentItem(
    LPCITEMIDLIST lpidl,
    LPITEMIDLIST& lpidlParent);
```

### <a name="parameters"></a>Parámetros

*lpidl*<br/>
[en] Un PIDL cuyo elemento primario se recuperará.

*lpidlParent*<br/>
[fuera] Una referencia a un PIDL donde el método almacenará el resultado.

### <a name="return-value"></a>Valor devuelto

El nivel del PIDL primario.

### <a name="remarks"></a>Observaciones

El nivel de un PIDL es relativo al escritorio. El PIDL de escritorio se considera que tiene un nivel de 0.

## <a name="cshellmanageritemfrompath"></a><a name="itemfrompath"></a>CShellManager::ItemFromPath

Recupera el puntero a una lista de identificadores de elemento (PIDL) del elemento identificado por una ruta de acceso de cadena.

```
HRESULT ItemFromPath(
    LPCTSTR lpszPath,
    LPITEMIDLIST& pidl);
```

### <a name="parameters"></a>Parámetros

*lpszPath*<br/>
[en] Cadena que especifica la ruta de acceso del elemento.

*pidl*<br/>
[fuera] Una referencia a un PIDL. El método utiliza este PIDL para almacenar el puntero a su valor devuelto.

### <a name="return-value"></a>Valor devuelto

Devuelve NOERROR si se realiza correctamente; un valor de error definido por OLE.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
