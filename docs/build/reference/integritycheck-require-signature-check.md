---
title: "-INTEGRITYCHECK (Requerir comprobación de firma) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7bf86676ecbc37e346f538d180612f21352fb48b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (Requerir control de signatura)
Especifica que la firma digital de la imagen binaria debe estar activada en tiempo de carga.  
  
```  
/INTEGRITYCHECK[:NO]  
```  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, **/INTEGRITYCHECK** está desactivada.  
  
 El **/INTEGRITYCHECK** opción conjuntos: en el encabezado PE del archivo DLL o el archivo ejecutable, una marca para que el Administrador de memoria comprobar una firma digital para cargar la imagen de Windows. Esta opción debe establecerse para los archivos DLL de 32 y 64 bits que implementan código en modo kernel cargado por determinadas características de Windows y se recomienda para todos los controladores de dispositivo en Windows Vista, [!INCLUDE[win7](../../build/includes/win7_md.md)], [!INCLUDE[win8](../../build/reference/includes/win8_md.md)], [!INCLUDE[winsvr08](../../build/reference/includes/winsvr08_md.md)] y [!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)]. Las versiones de Windows anteriores a Windows Vista omiten esta marca. Para obtener más información, consulte [archivos de forzar la integridad de firma del ejecutable Portable (PE)](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx).  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda el **propiedades de configuración** nodo.  
  
3.  Expanda el **vinculador** nodo.  
  
4.  Seleccione el **línea de comandos** página de propiedades.  
  
5.  En **opciones adicionales**, escriba `/INTEGRITYCHECK` o `/INTEGRITYCHECK:NO`.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [Archivos de integridad de firma del ejecutable Portable (PE) forzada](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)   
 [Tutorial de firma de código de modo kernel](http://msdn.microsoft.com/windows/hardware/gg487328.aspx)   
 [DLL de AppInit en Windows 7 y Windows Server 2008](http://msdn.microsoft.com/windows/hardware/gg463040.aspx)