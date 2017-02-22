---
title: "/CLRUNMANAGEDCODECHECK (Agregar SupressUnmanagedCodeSecurityAttribute) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/CLRUNMANAGEDCODECHECK"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/CLRUNMANAGEDCODECHECK (opción del vinculador)"
  - "-CLRUNMANAGEDCODECHECK (opción del vinculador)"
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# /CLRUNMANAGEDCODECHECK (Agregar SupressUnmanagedCodeSecurityAttribute)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\/**\/CLRUNMANAGEDCODECHECK** especifica si el vinculador aplicará <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> a las llamadas `PInvoke` generadas por el vinculador desde el código administrado a archivos DLL nativos.  
  
## Sintaxis  
  
```  
/CLRUNMANAGEDCODECHECK[:NO]  
```  
  
## Comentarios  
 De forma predeterminada, el vinculador aplica SuppressUnmanagedCodeSecurityAttribute a las llamadas `PInvoke` generadas por el vinculador.  Cuando **\/CLRUNMANAGEDCODECHECK** está activo, no se aplica SuppressUnmanagedCodeSecurityAttribute.  
  
 El vinculador sólo agrega el atributo a objetos que se compilan con **\/clr** o **\/clr:pure**.  El vinculador no genera llamadas `PInvoke` en objetos compilados con **\/clr:safe**.  Para obtener más información, vea [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 Una llamada `PInvoke` se genera mediante el vinculador cuando éste no encuentra un símbolo administrado que satisfaga una referencia desde un llamador administrado, pero sí que encuentra un símbolo nativo que satisface esa referencia.  Para obtener más información sobre `PInvoke`, vea [Llamar a funciones nativas desde código administrado](../../dotnet/calling-native-functions-from-managed-code.md).  
  
 Tenga en cuenta que si utiliza <xref:System.Security.AllowPartiallyTrustedCallersAttribute> en su código, debería establecer explícitamente **\/CLRUNMANAGEDCODECHECK**.  Si una imagen contiene los atributos SuppressUnmanagedCodeSecurity y AllowPartiallyTrustedCallers, se trata de una vulnerabilidad potencial de seguridad.  
  
 Vea [Security Optimizations](http://msdn.microsoft.com/es-es/cf255069-d85d-4de3-914a-e4625215a7c0) para obtener más información sobre las implicaciones de utilizar SuppressUnmanagedCodeSecurityAttribute.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el nodo **Vinculador**.  
  
4.  Seleccione la página de propiedades **Avanzadas**.  
  
5.  Modifique la propiedad **Comprobación de código no administrado CLR**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)