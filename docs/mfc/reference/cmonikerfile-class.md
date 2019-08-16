---
title: Clase CMonikerFile
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
ms.openlocfilehash: 56283b56a1c0832d34ce23c7db47c47d9480aec8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504567"
---
# <a name="cmonikerfile-class"></a>Clase CMonikerFile

Representa una secuencia de datos ( [IStream](/windows/win32/api/objidl/nn-objidl-istream)) denominada por un objeto [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker).

## <a name="syntax"></a>Sintaxis

```
class CMonikerFile : public COleStreamFile
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMonikerFile::CMonikerFile](#cmonikerfile)|Construye un objeto `CMonikerFile`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMonikerFile::Close](#close)|Desasocia y libera el flujo y libera el moniker.|
|[CMonikerFile::Detach](#detach)|Desasocia el `IMoniker` objeto de `CMonikerFile` este objeto.|
|[CMonikerFile::GetMoniker](#getmoniker)|Devuelve el moniker actual.|
|[CMonikerFile::Open](#open)|Abre el archivo especificado para obtener un flujo.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMonikerFile::CreateBindContext](#createbindcontext)|Obtiene el contexto de enlace o crea un contexto de enlace inicializado predeterminado.|

## <a name="remarks"></a>Comentarios

Un moniker contiene información muy similar a la ruta de acceso a un archivo. Si tiene un puntero a la interfaz de `IMoniker` un objeto moniker, puede obtener acceso al archivo identificado sin tener ninguna otra información específica sobre dónde se encuentra realmente el archivo.

Derivado de `COleStreamFile`, `CMonikerFile` toma un moniker o una representación de cadena que puede convertir en un moniker y enlaza con la secuencia para la que el moniker es un nombre. Después, puede leer y escribir en esa secuencia. El propósito real de `CMonikerFile` es proporcionar un acceso sencillo a `IStream`los nombres `IMoniker`de s, de modo que no tenga que enlazarse a un flujo usted mismo, `CFile` pero tenga la funcionalidad de la secuencia.

`CMonikerFile`no se puede utilizar para enlazar a nada que no sea un flujo. Si desea enlazar con el almacenamiento o un objeto, debe usar la `IMoniker` interfaz directamente.

Para obtener más información sobre las secuencias y monikers, vea [COleStreamFile](../../mfc/reference/colestreamfile-class.md) en la *referencia de MFC* y [IStream](/windows/win32/api/objidl/nn-objidl-istream) y [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) en el Windows SDK.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

`CMonikerFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole. h

##  <a name="close"></a>  CMonikerFile::Close

Llame a esta función para desasociar y liberar el flujo y liberar el moniker.

```
virtual void Close();
```

### <a name="remarks"></a>Comentarios

Se puede llamar a en secuencias no abiertas o ya cerradas.

##  <a name="cmonikerfile"></a>  CMonikerFile::CMonikerFile

Construye un objeto `CMonikerFile`.

```
CMonikerFile();
```

##  <a name="createbindcontext"></a>  CMonikerFile::CreateBindContext

Llame a esta función para crear un contexto de enlace inicializado predeterminado.

```
IBindCtx* CreateBindContext(CFileException* pError);
```

### <a name="parameters"></a>Parámetros

*pError*<br/>
Puntero a una excepción de archivo. En caso de que se produzca un error, se establecerá en la causa.

### <a name="return-value"></a>Valor devuelto

Puntero al contexto de enlace [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) con el que se va a enlazar si se realiza correctamente; de lo contrario, NULL. Si la instancia de se abrió con `IBindHost` una interfaz, el contexto `IBindHost`de enlace se recupera de. Si no hay ninguna `IBindHost` interfaz o la interfaz no devuelve un contexto de enlace, se crea un contexto de enlace. Para obtener una descripción de la interfaz [IBindHost](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775076\(v=vs.85\)) , vea el Windows SDK.

### <a name="remarks"></a>Comentarios

Un contexto de enlace es un objeto que almacena información sobre una operación de enlace de moniker determinada. Puede invalidar esta función para proporcionar un contexto de enlace personalizado.

##  <a name="detach"></a>  CMonikerFile::Detach

Llame a esta función para cerrar la secuencia.

```
BOOL Detach(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parámetros

*pError*<br/>
Puntero a una excepción de archivo. En caso de que se produzca un error, se establecerá en la causa.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

##  <a name="getmoniker"></a>  CMonikerFile::GetMoniker

Llame a esta función para recuperar un puntero al moniker actual.

```
IMoniker* GetMoniker() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a la interfaz de moniker actual ( [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)).

### <a name="remarks"></a>Comentarios

Puesto `CMonikerFile` que no es una interfaz, el puntero devuelto no incrementa el recuento de referencias (a través de [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)) y el moniker se libera cuando se libera el `CMonikerFile` objeto. Si desea conservar el moniker o liberarlo, debe `AddRef` hacerlo.

##  <a name="open"></a>CMonikerFile:: Open

Llame a esta función miembro para abrir un archivo o un objeto moniker.

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
Dirección URL o nombre de archivo del archivo que se va a abrir.

*pError*<br/>
Puntero a una excepción de archivo. En caso de que se produzca un error, se establecerá en la causa.

*pMoniker*<br/>
Puntero a la interfaz `IMoniker` de moniker que se va a usar para obtener un flujo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

No se puede usar el parámetro *lpszURL* en un equipo Macintosh. Solo la forma *pMoniker* de `Open` se puede usar en un equipo Macintosh.

Puede usar una dirección URL o un nombre de archivo para el parámetro *lpszURL* . Por ejemplo:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]

\- o -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]

## <a name="see-also"></a>Vea también

[COleStreamFile (clase)](../../mfc/reference/colestreamfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile (clase)](../../mfc/reference/casyncmonikerfile-class.md)
