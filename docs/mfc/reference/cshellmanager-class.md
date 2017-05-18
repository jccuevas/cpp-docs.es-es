---
title: Clase CShellManager | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CShellManager class
ms.assetid: f15c4c1a-6fae-487d-9913-9b7369b33da0
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 2bf6be5c0d106344024d32e90cc6cfb1e3299075
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cshellmanager-class"></a>Clase CShellManager
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
|[CShellManager::CopyItem](#copyitem)|Crea un nuevo PIDL y copie el PIDL proporcionado en él.|  
|[CShellManager::CreateItem](#createitem)|Crea un nuevo PIDL del tamaño especificado.|  
|[CShellManager::FreeItem](#freeitem)|Elimina el PIDL proporcionado.|  
|[CShellManager::GetItemCount](#getitemcount)|Devuelve el número de elementos en el PIDL proporcionado.|  
|[CShellManager::GetItemSize](#getitemsize)|Devuelve el tamaño de la PIDL proporcionado.|  
|[CShellManager::GetNextItem](#getnextitem)|Devuelve el siguiente elemento de la PIDL.|  
|[CShellManager::GetParentItem](#getparentitem)|Recupera el elemento primario del elemento proporcionado.|  
|[CShellManager::ItemFromPath](#itemfrompath)|Recupera el PIDL para el elemento identificado por la ruta de acceso proporcionada.|  
  
## <a name="remarks"></a>Comentarios  
 Los métodos de la `CShellManager` clase tratar todos los PIDL. Un PIDL es un identificador único para un objeto del shell.  
  
 No debería crear un `CShellManager` objeto manualmente. Se creará automáticamente por el marco de la aplicación. Sin embargo, debe llamar a [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) durante el proceso de inicialización de la aplicación. Para obtener un puntero al administrador de shell para la aplicación, llame a [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CShellManager](../../mfc/reference/cshellmanager-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxshellmanager.h  
  
##  <a name="browseforfolder"></a>CShellManager::BrowseForFolder  
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
 [out] `strOutFolder`  
 Cadena que se utiliza el método para almacenar la ruta de acceso de la carpeta seleccionada.  
  
 [in] `pWndParent`  
 Puntero a la ventana primaria.  
  
 [in] `lplszInitialFolder`  
 Cadena que contiene la carpeta que está seleccionada de forma predeterminada cuando se muestre el cuadro de diálogo.  
  
 [in] `lpszTitle`  
 El título del cuadro de diálogo.  
  
 [in] `ulFlags`  
 Marcadores que especifican las opciones del cuadro de diálogo. Consulte [BROWSEINFO](http://msdn.microsoft.com/library/windows/desktop/bb773205) la descripción detallada.  
  
 [out] `piFolderImage`  
 Un puntero al valor entero que el método escribe el índice de imagen de la carpeta seleccionada.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el usuario selecciona una carpeta en el cuadro de diálogo; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se llama a este método, la aplicación crea y muestra un cuadro de diálogo que permite al usuario seleccionar una carpeta. El método volverá a escribir la ruta de acceso de la carpeta en la `strOutFolder` parámetro.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo recuperar una referencia a un `CShellManager` objeto usando el `CWinAppEx::GetShellManager` método y cómo utilizar el `BrowseForFolder` método. Este fragmento de código forma parte de la [ejemplo Explorer](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_Explorer Nº&6;](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]  
  
##  <a name="concatenateitem"></a>CShellManager::ConcatenateItem  
 Crea una nueva lista que contiene dos PIDL.  
  
```  
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,  
    LPCITEMIDLIST pidl2);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pidl1`  
 El primer elemento.  
  
 [in] `pidl2`  
 El segundo elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la nueva lista de elementos si la función se realiza correctamente, de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Este método crea un nuevo [ITEMIDLIST](http://msdn.microsoft.com/library/windows/desktop/bb773321) lo suficientemente grande como para contener `pidl1` y `pidl2`. A continuación, copia `pidl1` y `pidl2` a la nueva lista.  
  
##  <a name="copyitem"></a>CShellManager::CopyItem  
 Copia una lista de elementos.  
  
```  
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pidlSource`  
 La lista de elementos original.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la lista de los elementos recién creado si se realiza correctamente; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 La lista de los elementos recién creado tiene el mismo tamaño que la lista de elementos de origen.  
  
##  <a name="createitem"></a>CShellManager::CreateItem  
 Crea un nuevo PIDL.  
  
```  
LPITEMIDLIST CreateItem(UINT cbSize);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `cbSize`  
 El tamaño de la lista de elementos.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la lista de elementos creados si es correcto; de lo contrario, `NULL`.  
  
##  <a name="cshellmanager"></a>CShellManager::CShellManager  
 Construye un objeto `CShellManager`.  
  
```  
CShellManager();
```  
  
### <a name="remarks"></a>Comentarios  
 En la mayoría de los casos, no es necesario crear un `CShellManager` directamente. De forma predeterminada, el marco de trabajo crea uno automáticamente. Para obtener un puntero a la `CShellManager`, llame a [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager). Si crea un `CShellManager` manualmente, se debe inicializar con el método [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager).  
  
##  <a name="freeitem"></a>CShellManager::FreeItem  
 Elimina una lista de elementos.  
  
```  
void FreeItem(LPITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pidl`  
 Para eliminar una lista de elementos.  
  
##  <a name="getitemcount"></a>CShellManager::GetItemCount  
 Devuelve el número de elementos en una lista de elementos.  
  
```  
UINT GetItemCount(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pidl`  
 Puntero a una lista de elementos.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos de la lista de elementos.  
  
##  <a name="getitemsize"></a>CShellManager::GetItemSize  
 Devuelve el tamaño de una lista de elementos.  
  
```  
UINT GetItemSize(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pidl`  
 Puntero a una lista de elementos.  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño de la lista de elementos.  
  
##  <a name="getnextitem"></a>CShellManager::GetNextItem  
 Recupera el siguiente elemento de un puntero a una lista de identificador de elementos (PIDL).  
  
```  
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pidl`  
 La lista de elementos para recorrer en iteración.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al siguiente elemento de la lista.  
  
### <a name="remarks"></a>Comentarios  
 Si no hay ninguna más elementos en la lista, este método devuelve `NULL`.  
  
##  <a name="getparentitem"></a>CShellManager::GetParentItem  
 Recupera al elemento primario de un puntero a una lista de identificador de elementos (PIDL).  
  
```  
int GetParentItem(
    LPCITEMIDLIST lpidl,  
    LPITEMIDLIST& lpidlParent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpidl`  
 Un PIDL cuyo elemento primario se va a recuperar.  
  
 [out] `lpidlParent`  
 Una referencia a un PIDL donde va a almacenar el resultado del método.  
  
### <a name="return-value"></a>Valor devuelto  
 El nivel del elemento primario PIDL.  
  
### <a name="remarks"></a>Comentarios  
 El nivel de un PIDL es con respecto al escritorio. El escritorio PIDL se considera que tiene un nivel de 0.  
  
##  <a name="itemfrompath"></a>CShellManager::ItemFromPath  
 Recupera el puntero a una lista de identificador de elementos (PIDL) desde el elemento identificado por una ruta de acceso de la cadena.  
  
```  
HRESULT ItemFromPath(
    LPCTSTR lpszPath,  
    LPITEMIDLIST& pidl);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszPath`  
 Cadena que especifica la ruta de acceso para el elemento.  
  
 [out] `pidl`  
 Una referencia a un PIDL. El método usa este PIDL para almacenar el puntero a su valor devuelto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `NOERROR` si es correcto; un valor de error definido por OLE.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)

