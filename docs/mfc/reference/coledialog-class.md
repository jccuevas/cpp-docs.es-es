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
ms.openlocfilehash: 6a1983d426e97dd8063aee2857dc36557aa20677
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366094"
---
# <a name="coledialog-class"></a>COleDialog (clase)

Proporciona funcionalidad común a los cuadros de diálogo para OLE.

## <a name="syntax"></a>Sintaxis

```
class COleDialog : public CCommonDialog
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDialog::GetLastError](#getlasterror)|Obtiene el código de error devuelto por el cuadro de diálogo.|

## <a name="remarks"></a>Observaciones

La biblioteca Microsoft Foundation Class proporciona `COleDialog`varias clases derivadas de:

- [COleInsertDialog](../../mfc/reference/coleinsertdialog-class.md)

- [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)

- [COleChangeIconDialog](../../mfc/reference/colechangeicondialog-class.md)

- [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

- [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)

- [COleUpdateDialog](../../mfc/reference/coleupdatedialog-class.md)

- [COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)

- [COlePropertiesDialog](../../mfc/reference/colepropertiesdialog-class.md)

- [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)

Para obtener más información acerca de los cuadros de diálogo específicos de OLE, vea el artículo [Cuadros](../../mfc/dialog-boxes-in-ole.md)de diálogo en OLE .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`COleDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs.h

## <a name="coledialoggetlasterror"></a><a name="getlasterror"></a>COleDialog::GetLastError

Llame `GetLastError` a la función miembro `DoModal` para obtener información de error adicional cuando devuelve IDABORT.

```
UINT GetLastError() const;
```

### <a name="return-value"></a>Valor devuelto

Los códigos `GetLastError` de error devueltos por dependen del cuadro de diálogo específico que se muestra.

### <a name="remarks"></a>Observaciones

Consulte `DoModal` la función miembro en las clases derivadas para obtener información acerca de mensajes de error específicos.

## <a name="see-also"></a>Consulte también

[Clase CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
