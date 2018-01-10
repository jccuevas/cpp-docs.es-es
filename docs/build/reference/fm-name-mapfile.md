---
title: -Fm (nombre de archivo de asignaciones) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /fm
dev_langs: C++
helpviewer_keywords:
- -Fm compiler option [C++]
- mapfiles [C++], creating linker
- files [C++], creating map
- Fm compiler option [C++]
- /Fm compiler option [C++]
ms.assetid: 8154448a-93a7-4546-8e4c-5c44d0aff45d
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0a5111291ea92b8650896faf3117f0056510e5ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fm-name-mapfile"></a>/Fm (Asignar nombre al archivo de asignaciones)
Indica al vinculador que genere un archivo de asignaciones que contiene una lista de segmentos en el orden en que aparecen en el archivo .exe correspondiente o DLL.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Fmpathname  
```  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, el archivo de asignaciones recibe el nombre de base del archivo de código fuente de C o C++ correspondiente con una. Extensión de un mapa.  
  
 Especificar **/Fm** tiene el mismo efecto que si se había especificado el [/MAP (Generar archivo de asignaciones)](../../build/reference/map-generate-mapfile.md) opción del vinculador.  
  
 Si especifica [/c (compilar sin vincular)](../../build/reference/c-compile-without-linking.md) para suprimir la vinculación, **/Fm** no tiene ningún efecto.  
  
 Símbolos globales en un archivo de asignaciones normalmente tienen uno o más caracteres de subrayado iniciales porque el compilador agrega un carácter de subrayado inicial a los nombres de variable. Muchos símbolos globales que aparecen en el archivo de asignaciones se utilizan internamente por el compilador y las bibliotecas estándar.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en la página de propiedades **Línea de comandos** .  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Archivo de salida (/ F) opciones](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Especificar la ruta de acceso](../../build/reference/specifying-the-pathname.md)