---
title: /INTEGRITYCHECK (Requerir control de signatura)
ms.date: 11/04/2016
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
ms.openlocfilehash: 1732c612501b66753635b272f94764975c555f75
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492844"
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (Requerir control de signatura)

Especifica que la firma digital de la imagen binaria debe estar activada en tiempo de carga.

```
/INTEGRITYCHECK[:NO]
```

## <a name="remarks"></a>Comentarios

De forma predeterminada, **/INTEGRITYCHECK** es OFF.

La opción **/INTEGRITYCHECK** establece (en el encabezado PE del archivo dll o el archivo ejecutable) una marca para que el administrador de memoria Compruebe una firma digital con el fin de cargar la imagen en Windows. Esta opción debe establecerse para los archivos dll de 32 y 64 bits que implementan código en modo kernel cargado por determinadas características de Windows y se recomienda para todos los controladores de dispositivos en Windows Vista, Windows 7, Windows 8, Windows Server 2008 y Windows Server 2012. Las versiones de Windows anteriores a Windows Vista omiten esta marca. Para obtener más información, vea [firma de integridad forzada de archivos ejecutables portátiles (PE)](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx).

### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Expanda el nodo **Propiedades de configuración**.

1. Expanda el nodo **Enlazador**.

1. Seleccione la página de propiedades **línea de comandos** .

1. En **opciones adicionales**, escriba `/INTEGRITYCHECK` o `/INTEGRITYCHECK:NO`.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)<br/>
[Firma de integridad forzada de archivos ejecutables portátiles (PE)](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)<br/>
[Requisitos de firma de código en modo kernel](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-)<br/>
[Archivos dll de AppInit y arranque seguro](/windows/win32/dlls/secure-boot-and-appinit-dlls)
