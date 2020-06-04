---
title: Clase CRecentFileList
ms.date: 11/04/2016
f1_keywords:
- CRecentFileList
- AFXADV/CRecentFileList
- AFXADV/CRecentFileList::CRecentFileList
- AFXADV/CRecentFileList::Add
- AFXADV/CRecentFileList::GetDisplayName
- AFXADV/CRecentFileList::GetSize
- AFXADV/CRecentFileList::ReadList
- AFXADV/CRecentFileList::Remove
- AFXADV/CRecentFileList::UpdateMenu
- AFXADV/CRecentFileList::WriteList
helpviewer_keywords:
- CRecentFileList [MFC], CRecentFileList
- CRecentFileList [MFC], Add
- CRecentFileList [MFC], GetDisplayName
- CRecentFileList [MFC], GetSize
- CRecentFileList [MFC], ReadList
- CRecentFileList [MFC], Remove
- CRecentFileList [MFC], UpdateMenu
- CRecentFileList [MFC], WriteList
ms.assetid: a77f0524-7584-4582-849a-7e97b76d186e
ms.openlocfilehash: a2102c6a39c14c548828e57ad1c49de6a5bc03dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370905"
---
# <a name="crecentfilelist-class"></a>Clase CRecentFileList

Admite el control de lista de los archivos utilizados más recientemente (MRU).

## <a name="syntax"></a>Sintaxis

```
class CRecentFileList
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRecentFileList::CRecentFileList](#crecentfilelist)|Construye un objeto `CRecentFileList`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRecentFileList::Add](#add)|Agrega un archivo a la lista de archivos MRU.|
|[CRecentFileList::GetDisplayName](#getdisplayname)|Proporciona un nombre para mostrar el menú de un nombre de archivo MRU.|
|[CRecentFileList::GetSize](#getsize)|Recupera el número de archivos de la lista de archivos MRU.|
|[CRecentFileList::ReadList](#readlist)|Lee la lista de archivos MRU del registro o . Archivo INI.|
|[CRecentFileList::Remove](#remove)|Elimina un archivo de la lista de archivos MRU.|
|[CRecentFileList::UpdateMenu](#updatemenu)|Actualiza la visualización del menú de la lista de archivos MRU.|
|[CRecentFileList::WriteList](#writelist)|Escribe la lista de archivos MRU del registro o . Archivo INI.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRecentFileList::operator \[\]](#operator_at)|Devuelve `CString` un objeto en una posición determinada.|

## <a name="remarks"></a>Observaciones

Los archivos se pueden agregar o eliminar de la lista de archivos MRU, la lista de archivos se puede leer o escribir en el registro o un archivo . INI y el menú que muestra la lista de archivos MRU se pueden actualizar.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CRecentFileList`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxadv.h

## <a name="crecentfilelistadd"></a><a name="add"></a>CRecentFileList::Add

Agrega un archivo a la lista de archivos (MRU) más reciente.

```
virtual void Add(LPCTSTR lpszPathName);

virtual void Add(
    LPCTSTR lpszPathName,
    LPCTSTR lpszAppID);

void Add(
    IShellItem* pItem,
    LPCTSTR lpszAppID);

void Add(
    IShellLink* pLink,
    LPCTSTR lpszAppID);

void Add(
    PIDLIST_ABSOLUTE pidl,
    LPCTSTR lpszAppID);
```

### <a name="parameters"></a>Parámetros

*lpszPathName*<br/>
Especifica el nombre de ruta que se agregará a la lista.

*lpszAppID*<br/>
Especifica el identificador de modelo de usuario de aplicación para la aplicación.

*pItem*<br/>
Especifica un puntero a Elemento de Shell que se agregará a la lista.

*pLink*<br/>
Especifica un puntero a Vínculo de vaciado que se agregará a la lista.

*pidl*<br/>
Especifica el IDLIST para el elemento de shell que se debe agregar a la carpeta de documentos reciente.

### <a name="remarks"></a>Observaciones

El nombre del archivo se agregará a la parte superior de la lista MRU. Si el nombre de archivo ya existe en la lista MRU, se moverá a la parte superior.

## <a name="crecentfilelistcrecentfilelist"></a><a name="crecentfilelist"></a>CRecentFileList::CRecentFileList

Construye un objeto `CRecentFileList`.

```
CRecentFileList(
    UINT nStart,
    LPCTSTR lpszSection,
    LPCTSTR lpszEntryFormat,
    int nSize,
    int nMaxDispLen = AFX_ABBREV_FILENAME_LEN);
```

### <a name="parameters"></a>Parámetros

*nEmpezar*<br/>
Desplazamiento para la numeración en la visualización del menú de la lista de archivos MRU (utilizado más recientemente).

*lpszSection*<br/>
Señala el nombre de la sección del registro o de la aplicación. INI donde se lee y/o escribe la lista de archivos MRU.

*lpszEntryFormat*<br/>
Señala una cadena de formato que se utilizará para los nombres de las entradas almacenadas en el registro o en la aplicación. Archivo INI.

*nTamaño*<br/>
Número máximo de archivos en la lista de archivos MRU.

*nMaxDispLen*<br/>
Longitud máxima, en caracteres, disponible para la visualización del menú de un nombre de archivo en la lista de archivos MRU.

### <a name="remarks"></a>Observaciones

La cadena de formato señalada por *lpszEntryFormat* debe contener "%d", que se utilizará para sustituir el índice de cada elemento MRU. Por ejemplo, si la `"file%d"` cadena de formato `file0`es, las entradas se denominarán , `file1`, etc.

## <a name="crecentfilelistgetdisplayname"></a><a name="getdisplayname"></a>CRecentFileList::GetDisplayName

Obtiene un nombre para mostrar para un archivo en la lista de archivos MRU, para su uso en la visualización de menús de la lista MRU.

```
virtual BOOL GetDisplayName(
    CString& strName,
    int nIndex,
    LPCTSTR lpszCurDir,
    int nCurDir,
    BOOL bAtLeastName = TRUE) const;
```

### <a name="parameters"></a>Parámetros

*strName*<br/>
Ruta completa del archivo cuyo nombre se mostrará en la lista de menús de archivos MRU.

*nIndex*<br/>
El índice de base cero del archivo en la lista de archivos MRU.

*lpszCurDir*<br/>
Cadena que contiene el directorio actual.

*nCurDir*<br/>
Longitud de la cadena de directorio actual.

*bAtLeastName*<br/>
Si es distinto de cero, indica que se debe devolver el nombre base del archivo, incluso si supera `CRecentFileList` la longitud de visualización máxima (se pasa como el *nMaxDispLen* parámetro al constructor).

### <a name="return-value"></a>Valor devuelto

**FALSE** si no hay ningún nombre de archivo en el índice especificado en la lista de archivos de uso más reciente (MRU).

### <a name="remarks"></a>Observaciones

Si el archivo está en el directorio actual, la función deja el directorio fuera de la pantalla. Si el nombre de archivo es demasiado largo, el directorio y la extensión se eliminan. Si el nombre de archivo sigue siendo demasiado largo, el nombre para mostrar se establece en una cadena vacía a menos que *bAtLeastName* sea distinto de cero.

## <a name="crecentfilelistgetsize"></a><a name="getsize"></a>CRecentFileList::GetSize

Recupera el número de archivos de la lista de archivos MRU.

```
int GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

El número de archivos de la lista de archivos más reciente (MRU).

## <a name="crecentfilelistoperator--"></a><a name="operator_at"></a>CRecentFileList::operator [ ]

El operador de`[]`subíndice sobrecargado `CString` ( ) devuelve un único especificado por el índice de base cero en *nIndex*.

```
CString& operator[ ](int nindex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice de `CString` base cero `CString`de a en un conjunto de s.

## <a name="crecentfilelistreadlist"></a><a name="readlist"></a>CRecentFileList::ReadList

Lee la lista de archivos más reciente (MRU) del registro o de la aplicación. Archivo INI.

```
virtual void ReadList();
```

## <a name="crecentfilelistremove"></a><a name="remove"></a>CRecentFileList::Remove

Elimina un archivo de la lista de archivos MRU.

```
virtual void Remove(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice de base cero del archivo que se va a quitar de la lista de archivos (MRU) utilizado más recientemente.

## <a name="crecentfilelistupdatemenu"></a><a name="updatemenu"></a>CRecentFileList::UpdateMenu

Actualiza la visualización del menú de la lista de archivos MRU.

```
virtual void UpdateMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Un puntero al objeto [CCmdUI](../../mfc/reference/ccmdui-class.md) para el menú de lista de archivos utilizado más recientemente (MRU).

## <a name="crecentfilelistwritelist"></a><a name="writelist"></a>CRecentFileList::WriteList

Escribe la lista de archivos (MRU) más reciente en el registro o en la aplicación. Archivo INI.

```
virtual void WriteList();
```

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
