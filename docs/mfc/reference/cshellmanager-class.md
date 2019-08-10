---
title: Clase CShellManager
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
ms.openlocfilehash: 14e8da573621f712ae9e27647122d305be54b7b0
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916680"
---
# <a name="cshellmanager-class"></a>Clase CShellManager

Implementa varios métodos que permiten trabajar con punteros en listas de identificadores (PIDL).

## <a name="syntax"></a>Sintaxis

```
class CShellManager : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CShellManager::CShellManager](#cshellmanager)|Construye un objeto `CShellManager`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CShellManager::BrowseForFolder](#browseforfolder)|Muestra un cuadro de diálogo que permite al usuario seleccionar una carpeta de Shell.|
|[CShellManager::ConcatenateItem](#concatenateitem)|Concatena dos PIDL.|
|[CShellManager::CopyItem](#copyitem)|Crea un nuevo PIDL y copia el PIDL proporcionado en él.|
|[CShellManager::CreateItem](#createitem)|Crea un nuevo PIDL del tamaño especificado.|
|[CShellManager::FreeItem](#freeitem)|Elimina el PIDL proporcionado.|
|[CShellManager::GetItemCount](#getitemcount)|Devuelve el número de elementos del PIDL proporcionado.|
|[CShellManager::GetItemSize](#getitemsize)|Devuelve el tamaño del PIDL proporcionado.|
|[CShellManager::GetNextItem](#getnextitem)|Devuelve el siguiente elemento de PIDL.|
|[CShellManager::GetParentItem](#getparentitem)|Recupera el elemento primario del elemento proporcionado.|
|[CShellManager::ItemFromPath](#itemfrompath)|Recupera el PIDL para el elemento identificado por la ruta de acceso proporcionada.|

## <a name="remarks"></a>Comentarios

Todos los métodos de `CShellManager` la clase se ocupan de PIDL. Un PIDL es un identificador único para un objeto de Shell.

No debe crear un `CShellManager` objeto manualmente. El marco de la aplicación lo creará automáticamente. Sin embargo, debe llamar a [CWinAppEx:: InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) durante el proceso de inicialización de la aplicación. Para obtener un puntero al administrador de Shell para la aplicación, llame a [CWinAppEx:: GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CShellManager](../../mfc/reference/cshellmanager-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxshellmanager. h

##  <a name="browseforfolder"></a>  CShellManager::BrowseForFolder

Muestra un cuadro de diálogo que permite al usuario seleccionar una carpeta de Shell.

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
enuncia Cadena utilizada por el método para almacenar la ruta de acceso de la carpeta seleccionada.

*pWndParent*<br/>
de Puntero a la ventana primaria.

*lplszInitialFolder*<br/>
de Cadena que contiene la carpeta seleccionada de forma predeterminada cuando se muestra el cuadro de diálogo.

*lpszTitle*<br/>
de Título del cuadro de diálogo.

*ulFlags*<br/>
de Marcas que especifican las opciones del cuadro de diálogo. Consulte [BROWSEINFO](/windows/desktop/api/shlobj_core/ns-shlobj_core-browseinfoa) para obtener una descripción detallada.

*piFolderImage*<br/>
enuncia Puntero al valor entero en el que el método escribe el índice de imagen de la carpeta seleccionada.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario selecciona una carpeta en el cuadro de diálogo; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Cuando se llama a este método, la aplicación crea y muestra un cuadro de diálogo que permite al usuario seleccionar una carpeta. El método escribirá la ruta de acceso de la carpeta en el parámetro *strOutFolder* .

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo recuperar una referencia a `CShellManager` un objeto mediante el `CWinAppEx::GetShellManager` método y cómo utilizar el `BrowseForFolder` método. Este fragmento de código forma parte del [ejemplo de explorador](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]

##  <a name="concatenateitem"></a>  CShellManager::ConcatenateItem

Crea una nueva lista que contiene dos PIDL.

```
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,
    LPCITEMIDLIST pidl2);
```

### <a name="parameters"></a>Parámetros

*pidl1*<br/>
de Primer elemento.

*pidl2*<br/>
de El segundo elemento.

### <a name="return-value"></a>Valor devuelto

Un puntero a la nueva lista de elementos si la función se ejecuta correctamente, de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Este método crea un nuevo [ITEMIDLIST](/windows/desktop/api/shtypes/ns-shtypes-itemidlist) lo suficientemente grande como para contener *pidl1* y *pidl2*. Después, copia *pidl1* y *pidl2* en la nueva lista.

##  <a name="copyitem"></a>  CShellManager::CopyItem

Copia una lista de elementos.

```
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```

### <a name="parameters"></a>Parámetros

*pidlSource*<br/>
de La lista de elementos original.

### <a name="return-value"></a>Valor devuelto

Puntero a la lista de elementos recién creada si se realiza correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

La lista de elementos recién creada tiene el mismo tamaño que la lista de elementos de origen.

##  <a name="createitem"></a>  CShellManager::CreateItem

Crea un nuevo PIDL.

```
LPITEMIDLIST CreateItem(UINT cbSize);
```

### <a name="parameters"></a>Parámetros

*cbSize*<br/>
de Tamaño de la lista de elementos.

### <a name="return-value"></a>Valor devuelto

Puntero a la lista de elementos creada si se realiza correctamente; de lo contrario, NULL.

##  <a name="cshellmanager"></a>  CShellManager::CShellManager

Construye un objeto `CShellManager`.

```
CShellManager();
```

### <a name="remarks"></a>Comentarios

En la mayoría de los casos, no es necesario crear `CShellManager` un directamente. De forma predeterminada, el marco de trabajo crea uno automáticamente. Para obtener un puntero a `CShellManager`, llame a [CWinAppEx:: GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager). Si crea `CShellManager` manualmente, debe inicializarlo con el método [CWinAppEx:: InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager).

##  <a name="freeitem"></a>  CShellManager::FreeItem

Elimina una lista de elementos.

```
void FreeItem(LPITEMIDLIST pidl);
```

### <a name="parameters"></a>Parámetros

*pidl*<br/>
de Lista de elementos que se va a eliminar.

##  <a name="getitemcount"></a>  CShellManager::GetItemCount

Devuelve el número de elementos de una lista de elementos.

```
UINT GetItemCount(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parámetros

*pidl*<br/>
de Puntero a una lista de elementos.

### <a name="return-value"></a>Valor devuelto

Número de elementos de la lista de elementos.

##  <a name="getitemsize"></a>  CShellManager::GetItemSize

Devuelve el tamaño de una lista de elementos.

```
UINT GetItemSize(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parámetros

*pidl*<br/>
de Puntero a una lista de elementos.

### <a name="return-value"></a>Valor devuelto

Tamaño de la lista de elementos.

##  <a name="getnextitem"></a>  CShellManager::GetNextItem

Recupera el siguiente elemento de un puntero a una lista de identificadores de elementos (PIDL).

```
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parámetros

*pidl*<br/>
de Lista de elementos que se va a iterar.

### <a name="return-value"></a>Valor devuelto

Puntero al siguiente elemento de la lista.

### <a name="remarks"></a>Comentarios

Si no hay más elementos en la lista, este método devuelve NULL.

##  <a name="getparentitem"></a>  CShellManager::GetParentItem

Recupera el elemento primario de un puntero a una lista de identificadores de elemento (PIDL).

```
int GetParentItem(
    LPCITEMIDLIST lpidl,
    LPITEMIDLIST& lpidlParent);
```

### <a name="parameters"></a>Parámetros

*lpidl*<br/>
de PIDL cuyo elemento primario se va A recuperar.

*lpidlParent*<br/>
enuncia Referencia a un PIDL donde el método almacenará el resultado.

### <a name="return-value"></a>Valor devuelto

Nivel del PIDL primario.

### <a name="remarks"></a>Comentarios

El nivel de un PIDL es relativo al escritorio. Se considera que el PIDL de escritorio tiene un nivel de 0.

##  <a name="itemfrompath"></a>  CShellManager::ItemFromPath

Recupera el puntero a una lista de identificadores de elemento (PIDL) del elemento identificado por una ruta de acceso de cadena.

```
HRESULT ItemFromPath(
    LPCTSTR lpszPath,
    LPITEMIDLIST& pidl);
```

### <a name="parameters"></a>Parámetros

*lpszPath*<br/>
de Cadena que especifica la ruta de acceso del elemento.

*pidl*<br/>
enuncia Una referencia a un PIDL. El método usa este PIDL para almacenar el puntero en su valor devuelto.

### <a name="return-value"></a>Valor devuelto

Devuelve un ERROR Si se realiza correctamente; un valor de error definido por OLE.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
