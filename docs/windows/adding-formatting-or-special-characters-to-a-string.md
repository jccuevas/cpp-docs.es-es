---
title: "Adding Formatting or Special Characters to a String | Microsoft Docs"
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
helpviewer_keywords: 
  - "special characters, adding to strings"
  - "ASCII characters, adding to strings"
  - "strings [C++], formatting"
  - "strings [C++], special characters"
ms.assetid: c40f394a-8b2c-4896-ab30-6922863ddbb5
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Adding Formatting or Special Characters to a String
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### Para agregar formato o caracteres especiales a una cadena  
  
1.  Abra la tabla de cadenas haciendo doble clic en su icono en la [Vista de recursos](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Seleccione la cadena que desee modificar.  
  
3.  En la [ventana Propiedades](../Topic/Properties%20Window.md), agregue al texto del cuadro **Caption** alguna de las secuencias de escape estándar que se enumeran a continuación y presione **ENTRAR**:  
  
    |Para obtener|Escriba|  
    |------------------|-------------|  
    |Nueva línea|\\n|  
    |Retorno de carro|\\r|  
    |Tab|\\t|  
    |Barra diagonal inversa \(\\\)|\\\\|  
    |Carácter ASCII|\\ddd \(notación octal\)|  
    |Alerta \(timbre\)|\\a|  
  
> [!NOTE]
>  El Editor de cadenas no admite todo el conjunto de caracteres ASCII de escape.  Sólo pueden utilizarse los incluidos en la lista anterior.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados \(los orientados a Common Language Runtime\), vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 **Requisitos**  
  
 Win32  
  
## Vea también  
 [String Editor](../mfc/string-editor.md)   
 [Cadenas](_win32_Strings)   
 [Acerca de cadenas](_win32_About_Strings_cpp)