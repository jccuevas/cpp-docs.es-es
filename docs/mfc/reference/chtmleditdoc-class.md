---
title: CHtmlEditDoc (clase)
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditDoc
- AFXHTML/CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::GetView
- AFXHTML/CHtmlEditDoc::IsModified
- AFXHTML/CHtmlEditDoc::OpenURL
helpviewer_keywords:
- CHtmlEditDoc [MFC], CHtmlEditDoc
- CHtmlEditDoc [MFC], GetView
- CHtmlEditDoc [MFC], IsModified
- CHtmlEditDoc [MFC], OpenURL
ms.assetid: b2cca61f-e5d6-4099-b0d1-46bf85f0bd64
ms.openlocfilehash: f468de46cf6d8a8bfcd60521df8b1076a98f0735
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285339"
---
# <a name="chtmleditdoc-class"></a>CHtmlEditDoc (clase)

Con [CHtmlEditView](../../mfc/reference/chtmleditview-class.md), proporciona la funcionalidad de la plataforma de edición WebBrowser en el contexto de la arquitectura de vista-documento MFC.

## <a name="syntax"></a>Sintaxis

```
class AFX_NOVTABLE CHtmlEditDoc : public CDocument
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CHtmlEditDoc::CHtmlEditDoc](#chtmleditdoc)|Construye un objeto `CHtmlEditDoc`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CHtmlEditDoc::GetView](#getview)|Recupera el `CHtmlEditView` objeto asociado a este documento.|
|[CHtmlEditDoc::IsModified](#ismodified)|Devuelve si el control WebBrowser de asociado de la vista contiene un documento que se ha modificado por el usuario.|
|[CHtmlEditDoc::OpenURL](#openurl)|Se abre una dirección URL.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`CHtmlEditDoc`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxhtml.h

##  <a name="chtmleditdoc"></a>  CHtmlEditDoc::CHtmlEditDoc

Construye un objeto `CHtmlEditDoc`.

```
CHtmlEditDoc();
```

##  <a name="getview"></a>  CHtmlEditDoc::GetView

Recupera el [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) objeto asociado a este documento.

```
virtual CHtmlEditView* GetView() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al documento `CHtmlEditView` objeto.

##  <a name="ismodified"></a>  CHtmlEditDoc::IsModified

Devuelve si el control WebBrowser de asociado de la vista contiene un documento que se ha modificado por el usuario.

```
virtual BOOL IsModified();
```

##  <a name="openurl"></a>  CHtmlEditDoc::OpenURL

Se abre una dirección URL.

```
virtual BOOL OpenURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Parámetros

*lpszURL*<br/>
Abra la dirección URL.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

## <a name="see-also"></a>Vea también

[Ejemplo HTMLEdit](../../visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
