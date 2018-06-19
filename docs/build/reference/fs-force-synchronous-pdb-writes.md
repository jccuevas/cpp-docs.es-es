---
title: -FS (forzar escrituras de PDB sincrónicas) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /FS
dev_langs:
- C++
helpviewer_keywords:
- -FS compiler option [C++]
- /FS compiler option [C++]
ms.assetid: b2caaffe-f6e1-4963-b068-648f06b105e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8565022a77742a1a8c7ed1f243a192d94c8627fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374796"
---
# <a name="fs-force-synchronous-pdb-writes"></a>/FS (forzar escrituras de PDB sincrónicas)
Fuerza que se escribe en el archivo de programa (PDB) de la base de datos, creado por [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) o [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md): se serialicen mediante MSPDBSRV. EXE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/FS  
```  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, cuando **/Zi** o **/Zi** se especifica, el compilador bloquea los archivos PDB para escribir información de tipo e información de depuración simbólica. Esto puede reducir significativamente el tiempo que tarda el compilador en generar la información de tipos cuando hay muchos tipos. Si otro proceso bloquea temporalmente el archivo PDB (por ejemplo, un programa antivirus), las escrituras del compilador pueden producir errores y puede aparecer un error irrecuperable. Este problema también puede ocurrir cuando varias copias de cl.exe tienen acceso al mismo archivo PDB, por ejemplo, si la solución tiene proyectos independientes que utilizan los mismos directorios intermedios o si están habilitados los directorios de salida y las compilaciones en paralelo. El **/FS** opción del compilador impide que el compilador bloquee el archivo PDB y fuerza las escrituras recorrer MSPDBSRV. EXE, que serializa el acceso. Esto puede prolongar las compilaciones y no evita todos los errores que pueden aparecer cuando varias instancias de cl.exe tienen acceso al archivo PDB al mismo tiempo. Recomendamos cambiar la solución de forma que los proyectos independientes escriban en ubicaciones intermedias y de salida separadas, o de forma que uno de los proyectos dependa del otro para forzar las compilaciones de proyecto serializadas.  
  
 El [/MP](../../build/reference/mp-build-with-multiple-processes.md) opción habilita **/FS** de forma predeterminada.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **C/C++** carpeta.  
  
3.  Seleccione el **línea de comandos** página de propiedades.  
  
4.  Modificar el **opciones adicionales** propiedad para incluir `/FS` y, a continuación, elija **Aceptar**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)