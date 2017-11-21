---
title: "R6025 de Error en tiempo de ejecución de C | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6025
dev_langs: C++
helpviewer_keywords: R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 06fd7aa6458a3c7e89d80146ec20a0e3f7587b4b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="c-runtime-error-r6025"></a>R6025 de Error en tiempo de ejecución de C
llamada de función virtual pura  
  
> [!NOTE]
>  Si aparece este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema interno. La razón más común de este error es un error en la aplicación o una instalación dañada.  
>   
>  Puede intentar seguir estos pasos para corregir este error:  
>   
>  -   Use la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para reparar o reinstalar el programa.  
> -   Comprobar **Windows Update** en el **el Panel de Control** las actualizaciones de software.  
> -   Busque una versión actualizada de la aplicación. Si el problema continúa, póngase en contacto con el proveedor de la aplicación.  
  
 **Información para programadores**  
  
 No se ha creado una instancia de ningún objeto para controlar la llamada de función virtual pura.  
  
 Este error se debe al llamar a una función virtual de una clase base abstracta a través de un puntero que se crea mediante una conversión al tipo de la clase derivada, pero en realidad es un puntero a la clase base. Esto puede ocurrir cuando se realiza la conversión de un **void\***  a un puntero a una clase cuando la **void\***  se creó durante la construcción de la clase base.  
  
 Para obtener más información, consulte el [soporte técnico de Microsoft](http://go.microsoft.com/fwlink/?LinkId=75220) sitio Web.