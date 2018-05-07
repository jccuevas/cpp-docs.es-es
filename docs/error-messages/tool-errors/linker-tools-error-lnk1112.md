---
title: Las herramientas del vinculador LNK1112 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1112
dev_langs:
- C++
helpviewer_keywords:
- LNK1112
ms.assetid: 425793d8-37e6-4072-9b6e-c3d4e9c12562
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd4af160607d75f036d25d21f5a95e753bddb3be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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