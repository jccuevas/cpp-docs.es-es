---
title: -CLRIMAGETYPE (especificar el tipo de imagen CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
dev_langs: C++
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b7d8edd6c9e62456e54ac6228f25d7f923a6813c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (Especificar tipo de imagen CLR)
```  
/CLRIMAGETYPE:{IJW|PURE|SAFE|SAFE32BITPREFERRED}  
```  
  
## <a name="remarks"></a>Comentarios  
 El vinculador acepta objetos nativos y también que se compilan mediante los objetos de MSIL [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), / CLR: pure o/CLR: safe. Las opciones del compilador **/clr:pure** y **/clr:safe** están en desuso en Visual Studio 2015. Cuando se pasan objetos mixtos en la misma compilación, la capacidad de comprobar el archivo de salida será, de forma predeterminada, igual al nivel inferior de la capacidad de comprobar los módulos de entrada. Por ejemplo, si pasa un módulo seguro y uno puro al vinculador, el archivo de salida será puro. Si se pasan una imagen nativa y una imagen de modo mixto (compilado mediante **/CLR**), la imagen resultante será una imagen de modo mixto.  
  
 Puede usar /CLRIMAGETYPE para especificar un nivel inferior de capacidad de comprobación si es lo que necesita.  
  
 En .NET 4.5, /CLRIMAGETYPE admite una opción de SAFE32BITPREFERRED. Esto establece (en el encabezado PE de la imagen) las marcas que indican que los objetos de MSIL son seguros y se pueden ejecutar en todas las plataformas, pero que se prefieren los entornos de ejecución de 32 bits. Esta opción permite que una aplicación se ejecute en plataformas ARM y también especifica que se debe ejecutar bajo WOW64 en los sistemas operativos de 64 bits, en lugar de utilizar el entorno de ejecución de 64 bits.  
  
 Cuando un .exe que se ha compilado con **/CLR** o **/CLR: pure** se ejecuta en un sistema operativo de 64 bits, la aplicación se ejecuta bajo WOW64, que permite que una aplicación de 32 bits para ejecutarse en un sistema operativo de 64 bits. De forma predeterminada, un .exe compilado mediante el uso de **/CLR: safe** se ejecuta bajo compatibilidad de 64 bits del sistema operativo. Sin embargo, es posible que la aplicación segura cargue un componente de 32 bits. En ese caso, una imagen segura que se ejecute bajo la compatibilidad de 64 bits del sistema operativo no podrá cargar la aplicación de 32 bits y se producirá un error. Para asegurarse de que una imagen segura continuará ejecutándose cuando cargue un componente de 32 bits en un sistema operativo de 64 bits, utilice la opción /CLRIMAGETYPE:SAFE32BITPREFERRED. Si el código no tiene que ejecutarse en plataformas ARM, puede especificar la opción /CLRIMAGETYPE:PURE para cambiar los metadatos (.corflags) y marcarla para que se ejecute bajo WOW64 (y sustituya su propio token de entrada):  
  
 **cl /clr:safe t.cpp /link /clrimagetype:pure /entry:?main@@$$HYMHXZ /subsystem:console**  
  
 Para obtener más información sobre cómo determinar el tipo de imagen de CLR de un archivo, consulte [/CLRHEADER](../../build/reference/clrheader.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda el **propiedades de configuración** nodo.  
  
3.  Expanda el **vinculador** nodo.  
  
4.  Seleccione el **avanzadas** página de propiedades.  
  
5.  Modificar el **tipo de imagen CLR** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)