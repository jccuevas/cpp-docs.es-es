---
title: Las herramientas del vinculador LNK1112 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1112
dev_langs:
- C++
helpviewer_keywords:
- LNK1112
ms.assetid: 425793d8-37e6-4072-9b6e-c3d4e9c12562
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a915768f0668a4ce276962f9eafd1f905980e2be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1112"></a>Error de las herramientas del vinculador LNK1112
tipo de máquina del módulo 'type1' en conflicto con tipo de máquina de destino 'type2'  
  
 Los archivos de objeto especificados como entrada se compilaron para distintos tipos de equipos.  
  
 Por ejemplo, si se intenta vincular un archivo objeto compilado con **/clr** y un archivo objeto compilado con **/clr:pure** (tipo de máquina CEE), el enlazador generará el error LNK1112.  
  
 De forma similar, si crea un módulo con el compilador [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] y otro módulo con el compilador x86 y se intenta vincularlos, el enlazador generará el error LNK1112.  
  
 Una de las razones posibles de este error es que está desarrollando una aplicación de 64 bits, pero no instaló uno de los compiladores de Visual C++ de 64 bits. En este caso, las configuraciones de 64 bits no estarán disponibles. Para corregir este problema, ejecute el instalador de Visual Studio e instale los componentes de C++ que faltan.  
  
 Este error también puede producirse si cambia la **Configuración de soluciones activas** en **Configuration Manager** y luego intenta compilar el proyecto antes de eliminar los archivos intermedios del proyecto. Para resolver este error, seleccione **Recompilar solución** en el menú **Compilar** . También puede seleccionar **Limpiar solución** en el menú **Compilar** y luego compile la solución.  
  
## <a name="see-also"></a>Vea también  
 [Errores y advertencias de las herramientas del vinculador](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)