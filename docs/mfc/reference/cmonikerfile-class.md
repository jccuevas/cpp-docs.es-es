---
title: CMonikerFile (clase)
ms.date: 11/04/2016
f1_keywords:
- CMonikerFile
- AFXOLE/CMonikerFile
- AFXOLE/CMonikerFile::CMonikerFile
- AFXOLE/CMonikerFile::Close
- AFXOLE/CMonikerFile::Detach
- AFXOLE/CMonikerFile::GetMoniker
- AFXOLE/CMonikerFile::Open
- AFXOLE/CMonikerFile::CreateBindContext
helpviewer_keywords:
- CMonikerFile [MFC], CMonikerFile
- CMonikerFile [MFC], Close
- CMonikerFile [MFC], Detach
- CMonikerFile [MFC], GetMoniker
- CMonikerFile [MFC], Open
- CMonikerFile [MFC], CreateBindContext
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
ms.openlocfilehash: ecffdb3a6f44f60004cf4f039bdab9c98e212ce1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338043"
---
# <a name="cmonikerfile-class"></a>CMonikerFile (clase)

Representa un flujo de datos ( [IStream](/windows/desktop/api/objidl/nn-objidl-istream)) llamado por un [IMoniker](/windows/desktop/api/objidl/nn-objidl-imoniker).

## <a name="syntax"></a>Sintaxis

```
class CMonikerFile : public COleStreamFile
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMonikerFile::CMonikerFile](#cmonikerfile)|Construye un objeto `CMonikerFile`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMonikerFile::Close](#close)|Desasocia y libera la secuencia y libera el moniker.|
|[CMonikerFile::Detach](#detach)|Desasocia el `IMoniker` desde este `CMonikerFile` objeto.|
|[CMonikerFile::GetMoniker](#getmoniker)|Devuelve el moniker actual.|
|[CMonikerFile::Open](#open)|Abre el archivo especificado para obtener una secuencia.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CMonikerFile::CreateBindContext](#createbindcontext)|Obtiene el contexto de enlace o crea un contexto de enlace inicializado de forma predeterminada.|

## <a name="remarks"></a>Comentarios

Un moniker contiene información muy similar a una ruta de acceso a un archivo. Si tiene un puntero a un objeto moniker `IMoniker` interfaz, puede obtener acceso al archivo identificado sin necesidad de cualquier otra información específica sobre donde se encuentra realmente el archivo.

Deriva `COleStreamFile`, `CMonikerFile` toma un moniker o una representación de cadena puede convertir en un moniker y se enlaza a la secuencia para que el moniker es un nombre. A continuación, puede leer y escribir en esa secuencia. El objetivo real de `CMonikerFile` es proporcionar un acceso sencillo a `IStream`s con el nombre `IMoniker`s por lo que no es necesario que enlazar a una secuencia usted mismo, aún tiene `CFile` funcionalidad en la secuencia.

`CMonikerFile` no se puede usar para enlazar a un valor distinto de una secuencia. Si desea enlazar a un objeto o de almacenamiento, debe usar el `IMoniker` interfaz directamente.

Para obtener más información sobre secuencias y monikers, consulte [COleStreamFile](../../mfc/reference/colestreamfile-class.md) en el *referencia de MFC* y [IStream](/windows/desktop/api/objidl/nn-objidl-istream) y [IMoniker](/windows/desktop/api/objidl/nn-objidl-imoniker) en el Windows SDK.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

`CMonikerFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

##  <a name="close"></a>  CMonikerFile::Close

Llame a esta función para separar y liberar la secuencia y para liberar el moniker.

```
virtual void Close();
```

### <a name="remarks"></a>Comentarios

Se puede llamar en secuencias no abiertos o cerrados ya.

##  <a name="cmonikerfile"></a>  CMonikerFile::CMonikerFile

Construye un objeto `CMonikerFile`.

```
CMonikerFile();
```

##  <a name="createbindcontext"></a>  CMonikerFile::CreateBindContext

Llame a esta función para crear un contexto de enlace inicializado de forma predeterminada.

```
IBindCtx* CreateBindContext(CFileException* pError);
```

### <a name="parameters"></a>Parámetros

*pError*<br/>
Un puntero a una excepción de archivo. Si se produce un error, se establecerá la causa.

### <a name="return-value"></a>Valor devuelto

Un puntero al contexto de enlace [IBindCtx](/windows/desktop/api/objidl/nn-objidl-ibindctx) para enlazar con si es correcto; de lo contrario, NULL. Si la instancia se abrió con una `IBindHost` interfaz, se recupera el contexto de enlace de la `IBindHost`. Si no hay ningún `IBindHost` interfaz o la interfaz no puede devolver un contexto de enlace, se crea un contexto de enlace. Para obtener una descripción de la [IBindHost](https://msdn.microsoft.com/library/ie/ms775076) de la interfaz, consulte el SDK de Windows.

### <a name="remarks"></a>Comentarios

Un contexto de enlace es un objeto que almacena información sobre una operación de enlace de moniker determinado. Se puede reemplazar esta función para proporcionar un contexto de enlace personalizada.

##  <a name="detach"></a>  CMonikerFile::Detach

Llame a esta función para cerrar la secuencia.

```
BOOL Detach(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parámetros

*pError*<br/>
Un puntero a una excepción de archivo. Si se produce un error, se establecerá la causa.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

##  <a name="getmoniker"></a>  CMonikerFile::GetMoniker

Llame a esta función para recuperar un puntero para el moniker actual.

```
IMoniker* GetMoniker() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la interfaz del moniker actual ( [IMoniker](/windows/desktop/api/objidl/nn-objidl-imoniker)).

### <a name="remarks"></a>Comentarios

Puesto que `CMonikerFile` no es una interfaz, el puntero devuelto no incrementa el recuento de referencias (a través de [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref)), y el moniker se libera cuando el `CMonikerFile` se libera el objeto. Si desea retener el moniker o liberar usted mismo, debe `AddRef` lo.

##  <a name="open"></a>  CMonikerFile::Open

Llame a esta función miembro para abrir un objeto de archivo o moniker.

```
virtual BOOL Open(
    LPCTSTR lpszURL,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszURL*<br/>
Una dirección URL o nombre de archivo del archivo que se puede abrir.

*pError*<br/>
Un puntero a una excepción de archivo. Si se produce un error, se establecerá la causa.

*pMoniker*<br/>
Un puntero a la interfaz de moniker `IMoniker` que se usará para obtener una secuencia.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El *lpszURL* parámetro no se puede usar en un equipo Macintosh. Solo el *pMoniker* forma de `Open` puede usarse en un equipo Macintosh.

Puede usar una dirección URL o un nombre de archivo para el *lpszURL* parámetro. Por ejemplo:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]

\- o -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]

## <a name="see-also"></a>Vea también

[COleStreamFile (clase)](../../mfc/reference/colestreamfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile (clase)](../../mfc/reference/casyncmonikerfile-class.md)
