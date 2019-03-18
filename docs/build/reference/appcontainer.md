---
title: /APPCONTAINER
ms.date: 11/04/2016
f1_keywords:
- /APPCONTAINER
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
ms.openlocfilehash: eb922a29b00fee63effae302505f25c98b04523e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820811"
---
# <a name="appcontainer"></a>/APPCONTAINER

Marca un ejecutable que se debe ejecutar en un contenedor de aplicaciones, por ejemplo, una aplicación de Microsoft Store o Windows Universal.

```

/APPCONTAINER[:NO]
```

## <a name="remarks"></a>Comentarios

Un ejecutable que tiene establecida la opción **/APPCONTAINER** solo puede ejecutarse en un contenedor de la aplicación, que es el entorno de aislamiento del proceso que se introdujo en Windows 8. Para las aplicaciones de Microsoft Store y universales de Windows, se debe establecer esta opción.

## <a name="see-also"></a>Vea también

[Opciones de EDITBIN](editbin-options.md)<br/>
[¿Qué es una aplicación de universal Windows?](/windows/uwp/get-started/universal-application-platform-guide)
