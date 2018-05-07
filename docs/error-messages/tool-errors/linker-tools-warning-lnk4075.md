---
title: Las herramientas del vinculador LNK4075 advertencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4075
dev_langs:
- C++
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4bd9a4ecdad30a0be2d45300367f6f79a65a6b31
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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