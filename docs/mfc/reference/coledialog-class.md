---
title: COleDialog (clase)
ms.date: 11/04/2016
f1_keywords:
- COleDialog
- AFXODLGS/COleDialog
- AFXODLGS/COleDialog::GetLastError
helpviewer_keywords:
- COleDialog [MFC], GetLastError
ms.assetid: b1ed0aca-3914-4b00-af34-4a4fb491aec7
ms.openlocfilehash: c798c1ad81395465e7aa5405ab786ddfb67b71d7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494710"
---
# <a name="coledialog-class"></a>COleDialog (clase)

Proporciona funcionalidad común a los cuadros de diálogo para OLE.

## <a name="syntax"></a>Sintaxis

```
class COleDialog : public CCommonDialog
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleDialog::GetLastError](#getlasterror)|Obtiene el código de error devuelto por el cuadro de diálogo.|

## <a name="remarks"></a>Comentarios

La biblioteca Microsoft Foundation Class proporciona varias clases derivadas de `COleDialog`:

- [COleInsertDialog](../../mfc/reference/coleinsertdialog-class.md)

- [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)

- [COleChangeIconDialog](../../mfc/reference/colechangeicondialog-class.md)

- [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

- [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)

- [COleUpdateDialog](../../mfc/reference/coleupdatedialog-class.md)

- [COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)

- [COlePropertiesDialog](../../mfc/reference/colepropertiesdialog-class.md)

- [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)

Para obtener más información acerca de los cuadros de diálogo específicos de OLE, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`COleDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs.h

##  <a name="getlasterror"></a>  COleDialog::GetLastError

Llame a la `GetLastError` función miembro para obtener información de error adicional cuando `DoModal` devuelve IDABORT.

```
UINT GetLastError() const;
```

### <a name="return-value"></a>Valor devuelto

Los códigos de error devueltos por `GetLastError` dependen en el cuadro de diálogo específico.

### <a name="remarks"></a>Comentarios

Consulte la `DoModal` función miembro en las clases derivadas para obtener información acerca de los mensajes de error específico.

## <a name="see-also"></a>Vea también

[CCommonDialog (clase)](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)

