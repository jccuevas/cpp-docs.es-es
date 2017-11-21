---
title: "-SECCIÓN (especificar atributos de sección) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /section
dev_langs: C++
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
ms.assetid: 92b69d81-e421-462e-b46f-7d0dff9b9d16
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e3fd7e844d77b9a92408c0708542a4f8f5edf304
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="section-specify-section-attributes"></a>/SECTION (Especificar los atributos de la sección)
```  
/SECTION:name,[[!]{DEKPRSW}][,ALIGN=#]  
```  
  
## <a name="remarks"></a>Comentarios  
 La opción/Section cambia los atributos de una sección reemplazando los atributos establecidos cuando se compiló el archivo .obj para la sección.  
  
 Una sección en un archivo de archivo ejecutable portable (PE) es prácticamente equivalente a un segmento o los recursos en un nuevo archivo ejecutable de (NE). Secciones contienen código o datos. A diferencia de los segmentos, las secciones son bloques de memoria contigua sin restricciones de tamaño. Algunas secciones contienen código o datos que el programa declara y utiliza directamente, mientras que otras secciones de datos se crean para el vinculador y el Administrador de bibliotecas (lib.exe) y contienen información fundamental para el sistema operativo. Para obtener más información sobre los archivos NE, consulte "Executable-File Header Format" (Q65122) del artículo de Knowledge Base. Encontrará artículos de Knowledge Base en MSDN Library o en [http://support.microsoft.com](http://support.microsoft.com).  
  
 Especifique un signo de dos puntos (:) y una sección *nombre*. El *nombre* distingue mayúsculas de minúsculas.  
  
 No utilice los siguientes nombres, tal y como se crearán un conflicto con los nombres estándar. Por ejemplo, .sdata se utiliza en plataformas RISC:  
  
-   .arch  
  
-   BSS  
  
-   .Data  
  
-   .edata  
  
-   .IData  
  
-   .pdata  
  
-   rdata  
  
-   .reloc  
  
-   .rsrc  
  
-   .sbss  
  
-   .sdata  
  
-   .srdata  
  
-   Text  
  
-   .XData  
  
 Especifique uno o más atributos de la sección. Los caracteres de atributo, que se muestran a continuación, no distinguen mayúsculas de minúsculas. Debe especificar todos los atributos que desea que la sección tener; el carácter de un atributo se omite hace bit del atributo se ha desactivado. Si no se especifica R, W o E, existente lectura, escritura o estado ejecutable permanece sin cambios.  
  
 Para invalidar un atributo, preceden su carácter con un signo de exclamación (!). A continuación se muestran los significados de los caracteres de atributo.  
  
|Carácter|Atributo|Significado|  
|---------------|---------------|-------------|  
|E|Ejecutar|La sección es ejecutable|  
|R|Leer|Permite operaciones de lectura en datos|  
|W|Write|Permite operaciones de escritura en los datos|  
|S|Compartido|Comparte la sección entre todos los procesos que cargan la imagen|  
|D|Descartable|Marca la sección como no descartable|  
|K|Almacenable en caché|Marca la sección como no almacenable en caché|  
|P|Paginable|Marca la sección como no paginable|  
  
 K y P tienen peculiar en que los indicadores de sección que les corresponden tienen un sentido negativo. Si se especifica uno de ellos en la sección .text (/ SECTION:. Text, K), no habrá ninguna diferencia en los indicadores de sección al ejecutar [DUMPBIN](../../build/reference/dumpbin-options.md) con el [/HEADERS](../../build/reference/headers.md) opción; ya implícitamente se almacenó en caché. Para quitar el valor predeterminado, especifique Text! K y DUMPBIN revelará las características de sección, incluyendo "No almacenado en caché."  
  
 Una sección del archivo PE que no tenga E, R o W establecido es probablemente no será válida.  
  
 La alineación *=#*  le permite especificar un valor de alineación para una sección concreta. Vea [/alinear](../../build/reference/align-section-alignment.md) para obtener más información.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en la página de propiedades **Línea de comandos** .  
  
4.  Escriba la opción en la **opciones adicionales** cuadro.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)