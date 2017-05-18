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
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9dee257bec0f09bd729bf10c4a1468ecb20dfa61
ms.openlocfilehash: 84dea754a1d2268c92e703dd04b0169ccc258ab3
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="linker-tools-warning-lnk4075"></a>Advertencia de las herramientas del vinculador LNK4075
se omite "opción1" debido a la especificación "opción2"  
  
 La segunda opción reemplaza la primera.  
  
 Se especifican las opciones del vinculador mutuamente excluyentes.  Examine las opciones del vinculador.  Se especifican las opciones del vinculador depende de cómo esté generando el proyecto.  
  
-   Si va a compilar en el entorno de desarrollo, busque en las páginas de propiedades vinculador para su proyecto y ver dónde se especifican las opciones del vinculador.  Consulte [trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md) para obtener más información.  
  
-   Si compila en la línea de comandos, examine las opciones del vinculador especificadas no existe.  
  
-   Si compila con scripts de generación, examine estos scripts para ver dónde se especifican estas opciones del vinculador.  
  
 Cuando encuentre la que se especifican las opciones del vinculador mutuamente excluyentes, quite una de las opciones del vinculador.  
  
 Algunos ejemplos concretos:  
  
-   Si vincula un módulo que se compiló con **/Zi**, que implica una opción interna del vinculador denominada /EDITANDCONTINUE y un módulo que se compiló con/OPT: REF, / OPT: ICF o/incremental: no, que no implica /EDITANDCONTINUE, obtendrá LNK4075.  Consulte [/Z7, / Zi, /ZI (formato de información de depuración)](../../build/reference/z7-zi-zi-debug-information-format.md) para obtener más información.
