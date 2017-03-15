---
title: "/ENTRY (S&#237;mbolo de punto de entrada) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/entry"
  - "VC.Project.VCLinkerTool.EntryPointSymbol"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ENTRY (opción del vinculador)"
  - "ENTRY (opción del vinculador)"
  - "-ENTRY (opción del vinculador)"
  - "dirección inicial"
ms.assetid: 26c62ba2-4f52-4882-a7bd-7046a0abf445
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /ENTRY (S&#237;mbolo de punto de entrada)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ENTRY:function  
```  
  
## Comentarios  
 donde:  
  
 *función*  
 Función que especifica una dirección de inicio definida por el usuario para una DLL o un archivo .exe.  
  
## Comentarios  
 La opción \/ENTRY especifica una función de punto de entrada como dirección inicial de un archivo .exe o DLL.  
  
 La función debe definirse con la convención de llamada `__stdcall`.  Los parámetros y el valor devuelto dependen de que el programa sea una aplicación de consola, una aplicación Windows o un archivo DLL.  Es recomendable permitir que el vinculador establezca el punto de entrada para que pueda inicializarse correctamente la biblioteca en tiempo de ejecución de C y puedan ejecutarse los constructores de C\+\+ para objetos estáticos.  
  
 De forma predeterminada, la dirección de inicio es un nombre de función de la biblioteca en tiempo de ejecución de C,  seleccionado por el vinculador en función de los atributos del programa, como se muestra en la tabla siguiente:  
  
|Nombre de la función|Predeterminado para|  
|--------------------------|-------------------------|  
|**mainCRTStartup** \(o **wmainCRTStartup**\)|Una aplicación que use \/SUBSYSTEM:**CONSOLE**; llama a **main** \(o **wmain**\)|  
|**WinMainCRTStartup** \(o **wWinMainCRTStartup**\)|Una aplicación que use \/SUBSYSTEM:**WINDOWS**; llama a `WinMain` \(o **wWinMain**\), que se debe definir con `__stdcall`|  
|**\_DllMainCRTStartup**|Una DLL; llama a `DllMain`, que se debe definir con `__stdcall`, siempre y cuando exista\)|  
  
 Si no se especifica la opción [\/DLL](../../build/reference/dll-build-a-dll.md) o [\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md), el vinculador seleccionará un subsistema y un punto de entrada, según se haya definido **main** o `WinMain`.  
  
 Las funciones **main**, `WinMain` y `DllMain` son los tres formatos del punto de entrada definido por el usuario.  
  
 Cuando se crea una imagen administrada, la función especificada con \/ENTRY debe tener una firma de \(LPVOID *var1*, DWORD *var2*, LPVOID *var3*\).  
  
 Para obtener información sobre la forma de definir su propio punto de entrada DllMain, vea [Comportamiento de la biblioteca en tiempo de ejecución](../../build/run-time-library-behavior.md).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Avanzadas**.  
  
4.  Modifique la propiedad **Punto de entrada**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)