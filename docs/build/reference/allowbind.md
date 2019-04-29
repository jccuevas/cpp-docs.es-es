---
title: /ALLOWBIND
ms.date: 11/04/2016
f1_keywords:
- /allowbind
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
ms.openlocfilehash: 4cb7e5a3627d865e2f2193dee096c72cced75f5f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273201"
---
# <a name="allowbind"></a>/ALLOWBIND

Especifica si se puede enlazar un archivo DLL.

```

/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Comentarios

El **/ALLOWBIND** opción establece un bit en el encabezado de un archivo DLL que se indica a Bind.exe que la imagen se puede enlazar. Enlace puede permitir que una imagen que se cargará más rápido cuando el cargador no tiene que reasignar y realizar la corrección de la dirección para cada DLL que se hace referencia. Quizás no desee que un archivo DLL se enlace si lo ha firmado digitalmente, el enlace invalida la firma. Enlace no tiene ningún efecto si la selección aleatoria de diseño de espacio de direcciones (ASLR) está habilitada para la imagen mediante el uso de **/DYNAMICBASE** en las versiones de Windows compatibles con ASLR.

Use **/ALLOWBIND: no** para impedir que el archivo DLL de enlace Bind.exe.

Para obtener más información, consulte el [/ALLOWBIND](allowbind-prevent-dll-binding.md) opción del vinculador.

## <a name="see-also"></a>Vea también

[Opciones de EDITBIN](editbin-options.md)
