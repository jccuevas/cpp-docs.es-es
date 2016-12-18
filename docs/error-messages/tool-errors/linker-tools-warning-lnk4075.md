---
title: "Advertencia de las herramientas del vinculador LNK4075 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4075"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4075"
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de las herramientas del vinculador LNK4075
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se omite "opción1" debido a la especificación "opción2"  
  
 La segunda opción reemplaza la primera.  
  
 Se están especificando opciones del vinculador mutuamente excluyentes.  Examine las opciones del vinculador.  Dónde se especifiquen opciones del vinculador depende de cómo se esté compilando el proyecto.  
  
-   Si se está compilando en el entorno de desarrollo, mire en las páginas de propiedades del vinculador correspondientes al proyecto y compruebe dónde se están especificando las dos opciones del vinculador.  Vea [Cómo: Especificar propiedades de proyecto con páginas de propiedades](../../misc/how-to-specify-project-properties-with-property-pages.md) para obtener más información.  
  
-   Si compila en la línea de comandos, examine las opciones del vinculador especificadas allí.  
  
-   Si compila con scripts de compilación, examine estos scripts para ver dónde se especifican estas opciones del vinculador.  
  
 Cuando averigüe dónde se especifican las opciones del vinculador mutuamente excluyentes, quite una de ellas.  
  
 Algunos ejemplos concretos:  
  
-   Si establece un vínculo con un módulo que se compiló con **\/ZI**, lo que implica una opción interna del vinculador llamada \/EDITANDCONTINUE, y otro módulo que se compiló con \/OPT:REF, \/OPT:ICF o \/INCREMENTAL:NO, que implica la desactivación de \/EDITANDCONTINUE, recibirá la advertencia LNK4075.  Para obtener más información, vea [\/Z7, \/Zi, \/ZI \(Formato de la información de depuración\)](../../build/reference/z7-zi-zi-debug-information-format.md).