---
title: CRecentFileList (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a6ac97eaa55dde337068e450c0223b4ec4409f8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393313"
---
# <a name="crecentfilelist-class"></a>CRecentFileList (clase)

Admite el control de lista de los archivos utilizados más recientemente (MRU).

## <a name="syntax"></a>Sintaxis

```
class CRecentFileList
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CRecentFileList::CRecentFileList](#crecentfilelist)|Construye un objeto `CRecentFileList`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CRecentFileList::Add](#add)|Agrega un archivo a la lista de archivos de elementos utilizados Recientemente.|
|[CRecentFileList::GetDisplayName](#getdisplayname)|Proporciona un nombre para mostrar del menú de un nombre de archivo MRU.|
|[CRecentFileList::GetSize](#getsize)|Recupera el número de archivos en la lista MRU.|
|[CRecentFileList::ReadList](#readlist)|Lee la lista de elementos utilizados Recientemente archivos desde el registro o. Archivo INI.|
|[CRecentFileList::Remove](#remove)|Quita un archivo de la lista MRU.|
|[CRecentFileList::UpdateMenu](#updatemenu)|Actualiza la presentación del menú de la lista de archivos de elementos utilizados Recientemente.|
|[CRecentFileList::WriteList](#writelist)|Escribe la lista de elementos utilizados Recientemente archivos del registro o. Archivo INI.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[[] CRecentFileList::operator](#operator_at)|Devuelve un `CString` objeto en una posición determinada.|

## <a name="remarks"></a>Comentarios

Pueden ser agrega o elimina de la lista MRU archivos, la lista de archivos se puede leer o escribir en el registro o una. Archivo INI y el menú de mostrar la lista de elementos utilizados Recientemente archivos se pueden actualizar.

Para obtener más información acerca de los elementos de menú de elementos utilizados Recientemente, vea

- Artículo de Knowledge Base Q243751: HOWTO: agregar controladores de comandos para elementos de menú de MRU de la aplicación MFC

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CRecentFileList`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxadv.h

##  <a name="add"></a>  CRecentFileList::Add

Agrega un archivo a la lista de archivos usa recientemente (MRU).

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
Especifica el nombre de ruta se agrega a la lista.

*lpszAppID*<br/>
Especifica el identificador de modelo de aplicación de usuario para la aplicación.

*pItem*<br/>
Especifica un puntero al elemento de Shell que debe agregarse a la lista.

*pLink*<br/>
Especifica un puntero al vínculo de Shell para agregarse a la lista.

*PIDL*<br/>
Especifica la lista de identificadores para el elemento de shell que debe agregarse a la carpeta de documentos recientes.

### <a name="remarks"></a>Comentarios

El nombre de archivo se agregará a la parte superior de la lista MRU. Si el nombre de archivo ya existe en la lista MRU, se moverá a la parte superior.

##  <a name="crecentfilelist"></a>  CRecentFileList::CRecentFileList

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

*Ncomenzar*<br/>
Desplazamiento de la numeración de la pantalla del menú de la lista de archivos MRU (usado más recientemente).

*lpszSection*<br/>
Señala al nombre de la sección de registro o de la aplicación. Archivo .ini donde la lista de archivos MRU es leída y/o escrita.

*lpszEntryFormat*<br/>
Apunta a una cadena de formato que se usará para los nombres de las entradas almacenadas en el registro o la aplicación. Archivo INI.

*nSize*<br/>
Número máximo de archivos en la lista MRU.

*nMaxDispLen*<br/>
Longitud máxima en caracteres, disponibles para la presentación de menú de un nombre de archivo en la lista MRU.

### <a name="remarks"></a>Comentarios

La cadena de formato que apunta *lpszEntryFormat* debe contener "%d", que se usará para sustituir el índice de cada elemento MRU. Por ejemplo, si la cadena de formato es `"file%d"` , a continuación, las entradas se denominará `file0`, `file1`, y así sucesivamente.

##  <a name="getdisplayname"></a>  CRecentFileList::GetDisplayName

Obtiene un nombre para mostrar de un archivo en la lista de archivos MRU, para su uso en la pantalla del menú de la lista MRU.

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
Ruta de acceso completa del archivo cuyo nombre es que se mostrará en la lista de archivos de elementos utilizados Recientemente del menú.

*nIndex*<br/>
Índice de base cero del archivo en la lista de archivos de elementos utilizados Recientemente.

*lpszCurDir*<br/>
Cadena que contiene el directorio actual.

*nCurDir*<br/>
Longitud de la cadena de directorio actual.

*bAtLeastName*<br/>
Si es distinto de cero, indica que se debe devolver el nombre base del archivo, incluso si supera la longitud máxima de visualización (pasado como el *nMaxDispLen* parámetro para el `CRecentFileList` constructor).

### <a name="return-value"></a>Valor devuelto

**FALSE** si no hay ningún nombre de archivo en el índice especificado en la lista de archivos usa recientemente (MRU).

### <a name="remarks"></a>Comentarios

Si el archivo está en el directorio actual, la función deja el directorio de la pantalla. Si el nombre de archivo es demasiado largo, se quitan el directorio y la extensión. Si el nombre de archivo sigue siendo demasiado largo, el nombre para mostrar se establece en una cadena vacía a menos que *bAtLeastName* es distinto de cero.

##  <a name="getsize"></a>  CRecentFileList::GetSize

Recupera el número de archivos en la lista MRU.

```
int GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

El número de archivos actual más archivos usados recientemente (MRU).

##  <a name="operator_at"></a>  [] CRecentFileList::operator

El subíndice sobrecargado (`[]`) operador devuelve un único `CString` especificada por el índice de base cero en *nIndex*.

```
CString& operator[ ](int nindex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de base cero de un `CString` en un conjunto de `CString`s.

##  <a name="readlist"></a>  CRecentFileList::ReadList

Lee la mayoría de la archivos usados recientemente (MRU) desde el registro o la aplicación. Archivo INI.

```
virtual void ReadList();
```

##  <a name="remove"></a>  CRecentFileList::Remove

Quita un archivo de la lista MRU.

```
virtual void Remove(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de base cero del archivo que se va a quitar de la lista de archivos usa recientemente (MRU).

##  <a name="updatemenu"></a>  CRecentFileList::UpdateMenu

Actualiza la presentación del menú de la lista de archivos de elementos utilizados Recientemente.

```
virtual void UpdateMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Un puntero a la [CCmdUI](../../mfc/reference/ccmdui-class.md) objeto para el menú de lista de usados recientemente (MRU) archivo.

##  <a name="writelist"></a>  CRecentFileList::WriteList

Escribe la mayoría de la archivos usados recientemente (MRU) en el registro o la aplicación. Archivo INI.

```
virtual void WriteList();
```

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



