---
title: Acceso a la biblioteca de tipos
ms.date: 11/04/2016
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
ms.openlocfilehash: 23d4675bd3638d2effd1b967f0729f9e70dac6de
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78867043"
---
# <a name="type-library-access"></a>Acceso a la biblioteca de tipos

Las bibliotecas de tipos exponen las interfaces de un control OLE a otras aplicaciones compatibles con OLE. Cada control OLE debe tener una biblioteca de tipos si se van a exponer una o más interfaces.

Las macros siguientes permiten que un control OLE proporcione acceso a su propia biblioteca de tipos:

### <a name="type-library-access"></a>Acceso a la biblioteca de tipos

|||
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|Declara una `GetTypeLib` función miembro de un control OLE (debe usarse en la declaración de clase).|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|Implementa una `GetTypeLib` función miembro de un control OLE (debe usarse en la implementación de la clase).|

##  <a name="declare_oletypelib"></a>DECLARE_OLETYPELIB

Declara el `GetTypeLib` función miembro de la clase de control.

```
DECLARE_OLETYPELIB(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Nombre de la clase de control relacionada con la biblioteca de tipos.

### <a name="remarks"></a>Observaciones

Use esta macro en el archivo de encabezado de clase del control.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

##  <a name="implement_oletypelib"></a>IMPLEMENT_OLETYPELIB

Implementa la función miembro `GetTypeLib` del control.

```
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
Nombre de la clase de control relacionada con la biblioteca de tipos.

*tlid*<br/>
Número de ID. de la biblioteca de tipos.

*wVerMajor*<br/>
Número de versión principal de la biblioteca de tipos.

*wVerMinor*<br/>
Número de versión secundaria de la biblioteca de tipos.

### <a name="remarks"></a>Observaciones

Esta macro debe aparecer en el archivo de implementación para cualquier clase de control que use la macro DECLARE_OLETYPELIB.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
