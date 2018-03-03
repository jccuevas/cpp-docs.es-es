---
title: Las herramientas del vinculador LNK4075 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4075
dev_langs:
- C++
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e8c3330e637ae0e0dce5e875fcc349c6deefcf27
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4075"></a>Advertencia de las herramientas del vinculador LNK4075
se omite "opción1" debido a la especificación "opción2"  
  
 La segunda opción reemplaza la primera.  
  
 Se especifican las opciones del vinculador mutuamente excluyentes.  Examine las opciones del vinculador.  Donde se especifican las opciones del vinculador depende de cómo va a compilar el proyecto.  
  
-   Si va a compilar en el entorno de desarrollo, buscar en las páginas de propiedades vinculador para el proyecto y ver dónde se especifican ambas opciones del vinculador.  Vea [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md) para obtener más información.  
  
-   Si se compila en la línea de comandos, examine las opciones del vinculador especificadas no existe.  
  
-   Si compila con scripts de compilación, examine las secuencias de comandos para ver dónde se especifican estas opciones del vinculador.  
  
 Cuando encuentre donde se especifican las opciones del vinculador mutuamente excluyentes, quite una de las opciones del vinculador.  
  
 Algunos ejemplos específicos:  
  
-   Si vincula un módulo que se compiló con **/Zi**, lo cual implica una opción interna del vinculador llama/EDITANDCONTINUE y un módulo que se compiló con/OPT: REF, / OPT: ICF o/incremental: no, que no implica ningún/EDITANDCONTINUE, que se van a obtener LNK4075.  Vea [/Z7, / Zi, /ZI (formato de información de depuración)](../../build/reference/z7-zi-zi-debug-information-format.md) para obtener más información.