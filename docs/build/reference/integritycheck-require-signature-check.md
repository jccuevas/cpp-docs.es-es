---
title: -INTEGRITYCHECK (requerir firma) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31df513a40b60fcb57c48f0d20e124fc77888d99
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703134"
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (Requerir control de signatura)

Especifica que la firma digital de la imagen binaria debe estar activada en tiempo de carga.

```
/INTEGRITYCHECK[:NO]
```

## <a name="remarks"></a>Comentarios

De forma predeterminada, **/INTEGRITYCHECK** está desactivada.

El **/INTEGRITYCHECK** conjuntos de opciones, en el encabezado PE del archivo DLL o el archivo ejecutable: una marca para el Administrador de memoria comprobar una firma digital para cargar la imagen de Windows. Esta opción debe establecerse para archivos DLL de 32 bits y 64 bits que implementan código en modo kernel cargado por determinadas características de Windows y se recomienda para todos los controladores de dispositivo en Windows Vista, Windows 7, Windows 8, Windows Server 2008 y Windows Server 2012. Las versiones de Windows anteriores a Windows Vista omiten esta marca. Para obtener más información, consulte [archivos forzada integridad firma del ejecutable Portable (PE)](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx).

### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).

1. Expanda el nodo **Propiedades de configuración**.

1. Expanda el **vinculador** nodo.

1. Seleccione el **línea de comandos** página de propiedades.

1. En **opciones adicionales**, escriba `/INTEGRITYCHECK` o `/INTEGRITYCHECK:NO`.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)<br/>
[Forzar la integridad de firma de archivos ejecutables portátiles (PE)](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)
[tutorial de firma de código de modo Kernel](https://msdn.microsoft.com/windows/hardware/gg487328.aspx)<br/>
[DLL de AppInit en Windows 7 y Windows Server 2008](https://msdn.microsoft.com/windows/hardware/gg463040.aspx)