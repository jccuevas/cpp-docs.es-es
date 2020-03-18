---
title: /ALLOWBIND
ms.date: 11/04/2016
f1_keywords:
- /allowbind_bind
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
ms.openlocfilehash: 4f5b662223914cbb4970188595afb52cc2500cd4
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440388"
---
# <a name="allowbind"></a>/ALLOWBIND

Especifica si se puede enlazar un archivo DLL.

```

/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Observaciones

La opción **/ALLOWBIND** establece un bit en el encabezado de un archivo DLL que indica a Bind. exe que la imagen se puede enlazar. El enlace puede permitir que una imagen se cargue más rápido cuando el cargador no tiene que volver a basar y realizar la corrección de direcciones para cada DLL a la que se hace referencia. Es posible que no desee que un archivo DLL esté enlazado si se ha firmado digitalmente: el enlace invalida la firma. El enlace no tiene ningún efecto si la selección aleatoria del diseño del espacio de direcciones (ASLR) está habilitada para la imagen mediante **/dynamicbase** en las versiones de Windows compatibles con ASLR.

Use **/ALLOWBIND: no** para evitar que BIND. exe enlace el archivo dll.

Para obtener más información, vea la opción [/ALLOWBIND](allowbind-prevent-dll-binding.md) del enlazador.

## <a name="see-also"></a>Consulte también

[Opciones de EDITBIN](editbin-options.md)
