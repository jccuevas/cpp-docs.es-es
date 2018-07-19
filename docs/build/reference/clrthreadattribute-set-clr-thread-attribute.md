---
title: -CLRTHREADATTRIBUTE (atributo de subproceso CLR conjunto) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.CLRThreadAttribute
dev_langs:
- C++
helpviewer_keywords:
- /CLRTHREADATTRIBUTE linker option
- -CLRTHREADATTRIBUTE linker option
ms.assetid: 4907e9ef-5031-446c-aecf-0a0b32fae1e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b83c3df380b07f125bad8426b9bf18b013b606c8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373428"
---
# <a name="clrthreadattribute-set-clr-thread-attribute"></a>/CLRTHREADATTRIBUTE (Establecer el atributo de subproceso de CLR)
Especificar explícitamente el atributo de subprocesamiento para el punto de entrada del programa CLR.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/CLRTHREADATTRIBUTE:{STA|MTA|NONE}  
```  
  
#### <a name="parameters"></a>Parámetros  
 MTA  
 Se aplica el atributo MTAThreadAttribute al punto de entrada del programa.  
  
 NINGUNO  
 Igual que si no se especifica/CLRTHREADATTRIBUTE.  Permite que Common Language Runtime (CLR) establecer el atributo de subprocesamiento predeterminado.  
  
 STA  
 Se aplica el atributo STAThreadAttribute al punto de entrada del programa.  
  
## <a name="remarks"></a>Comentarios  
 Establecer el atributo thread solo es válido cuando se genera un .exe, ya que puede afectar al punto de entrada del subproceso principal.  
  
 Si utiliza el punto de entrada predeterminado (main o wmain, por ejemplo), especifique el modelo de subprocesamiento mediante /CLRTHREADATTRIBUTE o colocando el atributo de subprocesamiento (STAThreadAttribute o MTAThreadAttribute) en la función de entrada predeterminada.  
  
 Si usa un punto de entrada no es el predeterminado, especifique el modelo de subprocesamiento mediante /CLRTHREADATTRIBUTE o colocando el subprocesamiento de atributo en la función de entrada no predeterminada y, a continuación, especifique el punto de entrada no predeterminada con [/Entry](../../build/reference/entry-entry-point-symbol.md) .  
  
 Si el modelo de subprocesamiento especificado en el código fuente no está de acuerdo con el modelo de subprocesamiento especificado con/CLRTHREADATTRIBUTE, el vinculador omite /CLRTHREADATTRIBUTE y aplica el modelo de subprocesamiento especificado en el código fuente.  
  
 Será necesario que utilice el subprocesamiento único, por ejemplo, si su programa de CLR hospeda un objeto COM que utiliza subprocesamiento único.  Si el programa de CLR utiliza subprocesamiento múltiple, no puede hospedar un objeto COM que utiliza subprocesamiento único.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda el **propiedades de configuración** nodo.  
  
3.  Expanda el **vinculador** nodo.  
  
4.  Seleccione el **avanzadas** página de propiedades.  
  
5.  Modificar el **CLR Thread Attribute** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRThreadAttribute%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)