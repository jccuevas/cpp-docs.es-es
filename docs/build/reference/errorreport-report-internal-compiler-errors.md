---
title: -errorReport (informar de errores internos del compilador) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.ErrorReporting
- /errorreport
dev_langs: C++
helpviewer_keywords:
- /errorReport compiler option [C++]
- -errorReport compiler option [C++]
ms.assetid: 819828f8-b0a5-412c-9c57-bf822f17e667
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9b34df09ca53441789fc90061748ad591149d6b2
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="errorreport-report-internal-compiler-errors"></a>/errorReport (Informar de los errores del compilador)
Permite proporcionar directamente a Microsoft información sobre los errores internos del compilador (ICE).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/errorReport:[ none | prompt | queue | send ]  
```  
  
## <a name="arguments"></a>Argumentos  
 **none**  
 No se recopilarán informes sobre errores internos del compilador ni se enviarán a Microsoft.  
  
 **prompt**  
 Pregunta si desea enviar un informe cuando recibe un error interno del compilador. **símbolo del sistema** es el valor predeterminado cuando se compila una aplicación en el entorno de desarrollo.  
  
 **queue**  
 Pone en cola el informe de error. Cuando inicie sesión con privilegios de administrador, aparece una ventana para que puede notificar los errores desde la última vez que se registraron en (no se le pedirá que envíe informes de errores más de una vez cada tres días). **cola** es el valor predeterminado cuando se compila una aplicación en un símbolo del sistema.  
  
 **send**  
 Envía automáticamente informes de errores internos del compilador a Microsoft si el informe está habilitado por la configuración del sistema informe de errores de Windows.  
  
## <a name="remarks"></a>Comentarios  
 Cuando el compilador no puede procesar un archivo de código fuente, se produce un error interno del compilador (ICE). Cuando se produce un ICE, el compilador no genera un archivo de salida ni otro tipo de diagnóstico útil que pueda usar para corregir el código.  
  
 En versiones anteriores, cuando se obtenía un ICE, solo se recomienda llamar a servicios de soporte técnico de Microsoft para informar del problema. Con **/errorReport**, puede proporcionar información de los ICE directamente a Microsoft. Sus informes de error pueden ayudar a mejorar las futuras versiones del compilador.  
  
 La capacidad de un usuario de enviar informes depende de los permisos de directiva de equipo y de usuario.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en el **avanzadas** página de propiedades.  
  
4.  Modificar el **informe de errores de** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ErrorReporting%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)