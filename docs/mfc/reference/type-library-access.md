---
title: Acceso a la biblioteca de tipos
ms.date: 11/04/2016
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
ms.openlocfilehash: 1794e16489ab48d919bbd4116588fba4b74b88d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372874"
---
# <a name="type-library-access"></a>Acceso a la biblioteca de tipos

Las bibliotecas de tipos exponen las interfaces de un control OLE a otras aplicaciones compatibles con OLE. Cada control OLE debe tener una biblioteca de tipos si se van a exponer una o varias interfaces.

Las macros siguientes permiten que un control OLE proporcione acceso a su propia biblioteca de tipos:

### <a name="type-library-access"></a>Acceso a la biblioteca de tipos

|||
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|Declara una `GetTypeLib` función miembro de un control OLE (debe usarse en la declaración de clase).|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|Implementa una `GetTypeLib` función miembro de un control OLE (debe usarse en la implementación de la clase).|

## <a name="declare_oletypelib"></a><a name="declare_oletypelib"></a>DECLARE_OLETYPELIB

Declara la `GetTypeLib` función miembro de la clase de control.

```
DECLARE_OLETYPELIB(class_name)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre de la clase de control relacionado con la biblioteca de tipos.

### <a name="remarks"></a>Observaciones

Utilice esta macro en el archivo de encabezado de clase de control.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="implement_oletypelib"></a><a name="implement_oletypelib"></a>IMPLEMENT_OLETYPELIB

Implementa la función `GetTypeLib` miembro del control.

```
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre de la clase de control relacionado con la biblioteca de tipos.

*tlid*<br/>
El número de ID de la biblioteca de tipos.

*wVerMajor*<br/>
El número de versión principal de la biblioteca de tipos.

*wVerMinor*<br/>
El número de versión secundaria de la biblioteca de tipos.

### <a name="remarks"></a>Observaciones

Esta macro debe aparecer en el archivo de implementación para cualquier clase de control que utilice la macro DECLARE_OLETYPELIB.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
