---
title: "-ENTRADA (símbolo de punto de entrada) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /entry
- VC.Project.VCLinkerTool.EntryPointSymbol
dev_langs:
- C++
helpviewer_keywords:
- starting address
- -ENTRY linker option
- /ENTRY linker option
- ENTRY linker option
ms.assetid: 26c62ba2-4f52-4882-a7bd-7046a0abf445
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5ebaf9a8723f06b6fab8577abf283f6eec69aa25
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="entry-entry-point-symbol"></a>/ENTRY (Símbolo de punto de entrada)
```  
/ENTRY:function  
```  
  
## <a name="remarks"></a>Comentarios  
 donde:  
  
 *function*  
 Dirección de una función que especifique un valor definido por el usuario de inicio para un archivo .exe o DLL.  
  
## <a name="remarks"></a>Comentarios  
 La opción/ENTRY especifica una función de punto de entrada como la dirección inicial para un archivo .exe o DLL.  
  
 La función debe estar definida para usar el `__stdcall` convención de llamada. Los parámetros y el valor devuelto dependen de si el programa es una aplicación de consola, una aplicación de windows o un archivo DLL. Se recomienda permitir que el vinculador establezca el punto de entrada para que la biblioteca de tiempo de ejecución de C se inicializó correctamente y constructores de C++ para objetos estáticos se ejecutan.  
  
 De forma predeterminada, la dirección de inicio es un nombre de función de la biblioteca de tiempo de ejecución de C. El vinculador selecciona según los atributos del programa, como se muestra en la tabla siguiente.  
  
|Nombre de la función|Valor predeterminado de|  
|-------------------|-----------------|  
|**mainCRTStartup** (o **wmainCRTStartup**)|Una aplicación que utiliza /SUBSYSTEM:CONSOLE; llamadas `main` (o `wmain`)|  
|**WinMainCRTStartup** (o **wWinMainCRTStartup**)|Una aplicación que use/SUBSYSTEM:**WINDOWS**; llamadas `WinMain` (o `wWinMain`), que se debe definir para usar`__stdcall`|  
|**_DllMainCRTStartup**|UN ARCHIVO DLL; llamadas `DllMain` si existe, que se debe definir para usar`__stdcall`|  
  
 Si el [/DLL](../../build/reference/dll-build-a-dll.md) o [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) no se especifica la opción, el vinculador seleccionará un subsistema y punto de entrada dependiendo de si `main` o `WinMain` está definido.  
  
 Las funciones `main`, `WinMain`, y `DllMain` son los tres formatos del punto de entrada definido por el usuario.  
  
 Cuando se crea una imagen administrada, la función especificada a/Entry debe tener una firma de (LPVOID *var1*, DWORD *var2*, LPVOID *var3*).  
  
 Para obtener información sobre cómo definir sus propias `DllMain` punto de entrada, consulte [archivos DLL y Visual C++ comportamiento de la biblioteca de tiempo de ejecución](../../build/run-time-library-behavior.md) .  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **avanzadas** página de propiedades.  
  
4.  Modificar el **punto de entrada** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)