---
title: CMonikerFile (Clase)
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
ms.openlocfilehash: fc74ad2499fcde63faa2c5859a87fd9ffd2846eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319783"
---
# <a name="cmonikerfile-class"></a>CMonikerFile (Clase)

Representa una secuencia de datos ( [IStream](/windows/win32/api/objidl/nn-objidl-istream)) denominada por un [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker).

## <a name="syntax"></a>Sintaxis

```
class CMonikerFile : public COleStreamFile
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMonikerFile::CMonikerFile](#cmonikerfile)|Construye un objeto `CMonikerFile`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMonikerFile::Cerrar](#close)|Separa y libera la secuencia y libera el moniker.|
|[CMonikerFile::Detach](#detach)|Separa el `IMoniker` objeto. `CMonikerFile`|
|[CMonikerFile::GetMoniker](#getmoniker)|Devuelve el moniker actual.|
|[CMonikerFile::Abrir](#open)|Abre el archivo especificado para obtener una secuencia.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMonikerFile::CreateBindContext](#createbindcontext)|Obtiene el contexto de enlace o crea un contexto de enlace inicializado predeterminado.|

## <a name="remarks"></a>Observaciones

Un moniker contiene información muy similar a un nombre de ruta de acceso a un archivo. Si tiene un puntero a la `IMoniker` interfaz de un objeto moniker, puede obtener acceso al archivo identificado sin tener ninguna otra información específica sobre dónde se encuentra realmente el archivo.

Derivado de `COleStreamFile` `CMonikerFile` , toma un moniker o una representación de cadena que puede convertir en un moniker y se enlaza a la secuencia para la que el moniker es un nombre. A continuación, puede leer y escribir en esa secuencia. El verdadero `CMonikerFile` propósito de es `IStream`proporcionar acceso `IMoniker`simple a s nombrado por s para que `CFile` no tenga que enlazar a una secuencia usted mismo, pero tener funcionalidad a la secuencia.

`CMonikerFile`no se puede utilizar para enlazar a otra cosa que no sea una secuencia. Si desea enlazar al almacenamiento o a un `IMoniker` objeto, debe utilizar la interfaz directamente.

Para obtener más información sobre secuencias y monikers, vea [COleStreamFile](../../mfc/reference/colestreamfile-class.md) en la referencia de *MFC* y [IStream](/windows/win32/api/objidl/nn-objidl-istream) e [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) en el Windows SDK.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

`CMonikerFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

## <a name="cmonikerfileclose"></a><a name="close"></a>CMonikerFile::Cerrar

Llame a esta función para separar y liberar la secuencia y liberar el moniker.

```
virtual void Close();
```

### <a name="remarks"></a>Observaciones

Se puede llamar en secuencias sin abrir o ya cerradas.

## <a name="cmonikerfilecmonikerfile"></a><a name="cmonikerfile"></a>CMonikerFile::CMonikerFile

Construye un objeto `CMonikerFile`.

```
CMonikerFile();
```

## <a name="cmonikerfilecreatebindcontext"></a><a name="createbindcontext"></a>CMonikerFile::CreateBindContext

Llame a esta función para crear un contexto de enlace inicializado predeterminado.

```
IBindCtx* CreateBindContext(CFileException* pError);
```

### <a name="parameters"></a>Parámetros

*pError*<br/>
Un puntero a una excepción de archivo. En caso de error, se establecerá en la causa.

### <a name="return-value"></a>Valor devuelto

Un puntero al contexto de enlace [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) para enlazar con si se realiza correctamente; NULL. Si la instancia se `IBindHost` abrió con una interfaz, `IBindHost`el contexto de enlace se recupera del archivo . Si no `IBindHost` hay ninguna interfaz o la interfaz no puede devolver un contexto de enlace, se crea un contexto de enlace. Para obtener una descripción de la [interfaz IBindHost,](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775076\(v=vs.85\)) consulte el Windows SDK.

### <a name="remarks"></a>Observaciones

Un contexto de enlace es un objeto que almacena información sobre una operación de enlace de moniker determinada. Puede invalidar esta función para proporcionar un contexto de enlace personalizado.

## <a name="cmonikerfiledetach"></a><a name="detach"></a>CMonikerFile::Detach

Llame a esta función para cerrar la secuencia.

```
BOOL Detach(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parámetros

*pError*<br/>
Un puntero a una excepción de archivo. En caso de error, se establecerá en la causa.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

## <a name="cmonikerfilegetmoniker"></a><a name="getmoniker"></a>CMonikerFile::GetMoniker

Llame a esta función para recuperar un puntero al moniker actual.

```
IMoniker* GetMoniker() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la interfaz de moniker actual ( [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)).

### <a name="remarks"></a>Observaciones

Puesto `CMonikerFile` que no es una interfaz, el puntero devuelto no incrementa el recuento `CMonikerFile` de referencias (a través de [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)) y el moniker se libera cuando se libera el objeto. Si quieres aferrarte al apodo o liberarlo `AddRef` tú mismo, debes hacerlo.

## <a name="cmonikerfileopen"></a><a name="open"></a>CMonikerFile::Abrir

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
Una url o nombre de archivo del archivo que se va a abrir.

*pError*<br/>
Un puntero a una excepción de archivo. En caso de error, se establecerá en la causa.

*pMoniker*<br/>
Un puntero a la `IMoniker` interfaz de moniker que se usará para obtener una secuencia.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El parámetro *lpszURL* no se puede utilizar en un Macintosh. Solo se puede utilizar `Open` la forma *pMoniker* de en un Macintosh.

Puede utilizar una dirección URL o un nombre de archivo para el parámetro *lpszURL.* Por ejemplo:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]

\- o -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]

## <a name="see-also"></a>Consulte también

[COleStreamFile (Clase)](../../mfc/reference/colestreamfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile (Clase)](../../mfc/reference/casyncmonikerfile-class.md)
