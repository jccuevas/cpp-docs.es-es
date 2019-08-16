---
title: Acceso a la biblioteca de tipos
ms.date: 11/04/2016
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
ms.openlocfilehash: 23d4675bd3638d2effd1b967f0729f9e70dac6de
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611531"
---
# <a name="type-library-access"></a>Acceso a la biblioteca de tipos

Bibliotecas de tipos exponen las interfaces de un control OLE para otras aplicaciones compatibles con OLE. Cada control OLE debe tener una biblioteca de tipos si una o más interfaces deben exponerse.

Las macros siguientes permiten un control OLE proporcionar acceso a su propia biblioteca de tipos:

### <a name="type-library-access"></a>Acceso a la biblioteca de tipos

|||
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|Declara un `GetTypeLib` función miembro de un control OLE (debe usarse en la declaración de clase).|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|Implementa un `GetTypeLib` función miembro de un control OLE (debe usarse en la implementación de la clase).|

##  <a name="declare_oletypelib"></a>  DECLARE_OLETYPELIB

Declara el `GetTypeLib` función miembro de la clase del control.

```
DECLARE_OLETYPELIB(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre de la clase de control relacionada con la biblioteca de tipos.

### <a name="remarks"></a>Comentarios

Use esta macro en el archivo de encabezado de la clase de control.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

##  <a name="implement_oletypelib"></a>  IMPLEMENT_OLETYPELIB

Implementa el control `GetTypeLib` función miembro.

```
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre de la clase de control relacionada con la biblioteca de tipos.

*tlid*<br/>
El número de Id. de la biblioteca de tipos.

*wVerMajor*<br/>
El número de versión principal de biblioteca de tipos.

*wVerMinor*<br/>
El número de versión secundaria de biblioteca de tipos.

### <a name="remarks"></a>Comentarios

Esta macro debe aparecer en el archivo de implementación para cualquier clase de control que utiliza el declare_oletypelib (macro).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="see-also"></a>Vea también

[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
