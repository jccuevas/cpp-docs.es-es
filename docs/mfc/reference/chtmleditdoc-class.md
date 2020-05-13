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
ms.openlocfilehash: 8b500f651da1a73040fdb0469f2f023babe25e85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352176"
---
# <a name="chtmleditdoc-class"></a>CHtmlEditDoc (clase)

Con [CHtmlEditView](../../mfc/reference/chtmleditview-class.md), proporciona la funcionalidad de la plataforma de edición WebBrowser en el contexto de la arquitectura de vista de documento MFC.

## <a name="syntax"></a>Sintaxis

```
class AFX_NOVTABLE CHtmlEditDoc : public CDocument
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHtmlEditDoc::CHtmlEditDoc](#chtmleditdoc)|Construye un objeto `CHtmlEditDoc`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHtmlEditDoc::GetView](#getview)|Recupera el `CHtmlEditView` objeto adjunto a este documento.|
|[CHtmlEditDoc::IsModified](#ismodified)|Devuelve si el control WebBrowser de la vista asociada contiene un documento modificado por el usuario.|
|[CHtmlEditDoc::OpenURL](#openurl)|Abre una dirección URL.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`CHtmlEditDoc`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxhtml.h

## <a name="chtmleditdocchtmleditdoc"></a><a name="chtmleditdoc"></a>CHtmlEditDoc::CHtmlEditDoc

Construye un objeto `CHtmlEditDoc`.

```
CHtmlEditDoc();
```

## <a name="chtmleditdocgetview"></a><a name="getview"></a>CHtmlEditDoc::GetView

Recupera el [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) objeto asociado a este documento.

```
virtual CHtmlEditView* GetView() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al `CHtmlEditView` objeto del documento.

## <a name="chtmleditdocismodified"></a><a name="ismodified"></a>CHtmlEditDoc::IsModified

Devuelve si el control WebBrowser de la vista asociada contiene un documento modificado por el usuario.

```
virtual BOOL IsModified();
```

## <a name="chtmleditdocopenurl"></a><a name="openurl"></a>CHtmlEditDoc::OpenURL

Abre una dirección URL.

```
virtual BOOL OpenURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Parámetros

*lpszURL*<br/>
Dirección URL que se va a abrir.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="see-also"></a>Consulte también

[Ejemplo de HTMLEdit](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
