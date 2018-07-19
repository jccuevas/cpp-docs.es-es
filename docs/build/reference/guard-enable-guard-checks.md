---
title: -PROTECCIÓN (habilitar comprobaciones de restricción) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 72758e23-70ac-4616-94d7-d767477406d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d05dd4f9d213c3d2729459486a9d0cfdbd79110
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375261"
---
# <a name="guard-enable-guard-checks"></a>/GUARD (habilitar comprobaciones de restricción)
Especifica la compatibilidad con las comprobaciones de Protección de flujo de control en la imagen ejecutable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/GUARD:{CF|NO}  
```  
  
## <a name="remarks"></a>Comentarios  
 Cuando se especifica /GUARD:CF, el vinculador modifica el encabezado de un archivo .dll o .exe para indicar la compatibilidad con las comprobaciones en tiempo de ejecución de Protección de flujo de Control (CFG). El vinculador también agrega los datos requeridos de dirección de destino del flujo de control al encabezado. De forma predeterminada, /GUARD:CF está deshabilitada. Se puede deshabilitar explícitamente mediante el uso de /GUARD:NO. Para que sea eficaz, / Guard: CF también requiere la [/DYNAMICBASE (aleatorio de diseño de espacio de dirección de uso)](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) opción del vinculador, que está habilitada de forma predeterminada.  
  
 Cuando se compila código fuente mediante el uso de la [/Guard: CF](../../build/reference/guard-enable-control-flow-guard.md) opción, el compilador analiza el flujo de control examinando todas las llamadas indirectas de posibles direcciones de destino. El compilador inserta código para comprobar que la dirección de destino de una instrucción de llamada indirecta está en la lista de direcciones de destino conocidas en tiempo de ejecución. Si un programa no supera una comprobación de CFG en tiempo de ejecución, los sistemas operativos compatibles con CFG lo detienen. Esto hace más difícil que un atacante pueda ejecutar código malintencionado mediante el uso de datos dañados para cambiar un destino de llamada.  
  
 La opción /GUARD:CF debe especificarse tanto en el compilador como en el vinculador para crear imágenes ejecutables con protección de flujo de control (CFG). El código compilado pero no vinculado mediante /GUARD:CF aumenta el costo de comprobaciones en tiempo de ejecución, pero no habilita la protección CFG. Cuando se especifica la opción/Guard: CF para el `cl` comando para compilar y vincular en un solo paso, el compilador pasa la marca al vinculador. Cuando el **protección de flujo de Control** propiedad está establecida en Visual Studio, se pasa la opción/Guard: CF para el compilador y el vinculador. Cuando se han compilado por separado los archivos objeto o en bibliotecas, la opción debe especificarse explícitamente en el `link` comando.  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda **propiedades de configuración**, **vinculador**, **línea de comandos**.  
  
3.  En **opciones adicionales**, escriba `/GUARD:CF`.  
  
## <a name="see-also"></a>Vea también  
 [/Guard (habilitar Control de flujo de protección)](../../build/reference/guard-enable-control-flow-guard.md)   
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)