---
title: / INTEGRITYCHECK | Documentos de Microsoft
ms.custom: ''
ms.date: 12/28/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /INTEGRITYCHECK
dev_langs:
- C++
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b0adf9add2d191ae89aec0a5d756ade8e9f7725
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

Especifica que la firma digital de la imagen binaria debe estar activada en tiempo de carga.

> **/ INTEGRITYCHECK**[**: N**]

## <a name="remarks"></a>Comentarios

En el encabezado del archivo DLL o el archivo ejecutable, esta opción establece una marca que requiere una comprobación de firma digital mediante el Administrador de memoria para cargar la imagen de Windows. Las versiones de Windows anteriores a Windows Vista omiten esta marca. Esta opción debe establecerse para archivos DLL de 64 bits que implementan código en modo kernel y se recomienda para todos los controladores de dispositivo. Para obtener más información, consulte [requisitos de firma de código de modo Kernel](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-).

## <a name="see-also"></a>Vea también

[Opciones de EDITBIN](../../build/reference/editbin-options.md)  
