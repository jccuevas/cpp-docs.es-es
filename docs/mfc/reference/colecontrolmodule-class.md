---
title: COleControlModule (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- OleControlModule
dev_langs:
- C++
helpviewer_keywords:
- OLE control modules [MFC]
- MFC ActiveX controls [MFC], OLE control modules
- COleControlModule class [MFC]
- control modules [MFC]
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 83c7e9bc265870e6099c231f8e15ec5e37902c55
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069300"
---
# <a name="colecontrolmodule-class"></a>COleControlModule (clase)

La clase base de la que se deriva un objeto de módulo de control OLE.

## <a name="syntax"></a>Sintaxis

```
class COleControlModule : public CWinApp
```

## <a name="remarks"></a>Comentarios

Esta clase proporciona funciones miembro para inicializar el módulo de control. Cada módulo de control OLE que usa Microsoft Foundation classes solo puede contener un objeto derivado de `COleControlModule`. Este objeto se crea cuando se crean otros objetos globales de C++. Declarar la derivada `COleControlModule` objeto en el nivel global.

Para obtener más información sobre el uso de la `COleControlModule` de clases, vea el [CWinApp](../../mfc/reference/cwinapp-class.md) clase y el artículo [controles ActiveX](../../mfc/mfc-activex-controls.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

[CWinApp](../../mfc/reference/cwinapp-class.md)

`COleControlModule`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxctl.h

## <a name="see-also"></a>Vea también

[Ejemplo de MFC TESTHELP](../../visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)

