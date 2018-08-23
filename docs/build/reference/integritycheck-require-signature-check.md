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
ms.openlocfilehash: 5a10594391b0f3be490608f7dfa006b0c32aa2e0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609285"
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
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el **vinculador** nodo.  
  
4.  Seleccione el **línea de comandos** página de propiedades.  
  
5.  En **opciones adicionales**, escriba `/INTEGRITYCHECK` o `/INTEGRITYCHECK:NO`.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [Forzada archivos de la integridad de firma del ejecutable Portable (PE)](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)   
 [Tutorial sobre la firma de código de modo kernel](http://msdn.microsoft.com/windows/hardware/gg487328.aspx)   
 [DLL de AppInit en Windows 7 y Windows Server 2008](http://msdn.microsoft.com/windows/hardware/gg463040.aspx)