---
title: "/INTEGRITYCHECK (Requerir control de signatura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /INTEGRITYCHECK (Requerir control de signatura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica que la firma digital de la imagen binaria debe estar activada en tiempo de carga.  
  
```  
/INTEGRITYCHECK[:NO]  
```  
  
## Comentarios  
 La opción **\/INTEGRITYCHECK** está desactivada de manera predeterminada.  
  
 La opción **\/INTEGRITYCHECK** establece \(en el encabezado PE del archivo DLL o del archivo ejecutable\) una marca para que el administrador de memoria compruebe si existe una signatura digital para cargar la imagen en Windows.  Esta opción debe establecerse para los archivos DLL de 32 y 64 bits que implementan código en modo kernel cargado por determinadas características de Windows y se recomienda para todos los controladores de dispositivo en Windows Vista, [!INCLUDE[win7](../../build/includes/win7_md.md)], [!INCLUDE[win8](../../build/includes/win8_md.md)], [!INCLUDE[winsvr08](../../build/includes/winsvr08_md.md)] y [!INCLUDE[winserver8](../../build/includes/winserver8_md.md)].  Las versiones de Windows anteriores a Windows Vista omiten esta marca.  Para obtener más información, vea el articulo acerca de la [firma de integridad forzada de archivos ejecutables portátiles \(PE\)](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx).  
  
### Para establecer esta opción del vinculador en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el nodo **Vinculador**.  
  
4.  Seleccione la página de propiedades **Línea de comandos**.  
  
5.  En **Opciones adicionales**, escriba `/INTEGRITYCHECK` o `/INTEGRITYCHECK:NO`.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [Firma de integridad forzada de archivos ejecutables portátiles \(PE\)](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)   
 [Tutorial sobre la firma de código en modo Kernel](http://msdn.microsoft.com/windows/hardware/gg487328.aspx)   
 [Archivos DLL de AppInit en Windows 7 y Windows Server 2008](http://msdn.microsoft.com/windows/hardware/gg463040.aspx)