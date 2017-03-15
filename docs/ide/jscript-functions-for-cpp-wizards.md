---
title: "Funciones de JScript para los asistentes de C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "métodos de JScript para asistentes"
  - "métodos de JScript para asistentes, crear asistentes de C++"
ms.assetid: f3046c56-cf67-4aaa-919e-8c066bfb6760
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Funciones de JScript para los asistentes de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

|||  
|-|-|  
|[AddATLSupportToProject](../ide/addatlsupporttoproject.md)|Agrega compatibilidad con ATL a un proyecto MFC.|  
|[AddCoclassFromFile](../ide/addcoclassfromfile.md)|Representa e inserta en el archivo .idl del proyecto un archivo de plantilla que contiene una coclase.|  
|[AddCommonConfig](../ide/addcommonconfig.md)|Agrega las configuraciones predeterminadas al proyecto.|  
|[AddFilesToProject](../ide/addfilestoproject.md)|Agrega todos los archivos al proyecto según la lista del archivo Templates.inf.|  
|[AddInterfaceFromFile](../ide/addinterfacefromfile.md)|Representa e inserta en el archivo IDL del proyecto un archivo de plantilla que contiene una interfaz.|  
|[CanAddATLClass](../ide/canaddatlclass.md)|El asistente llama a esta función para comprobar si el proyecto es compatible con el asistente para código que va a ejecutarse \(es decir, si puede aceptar una clase ATL\).<br /><br /> El asistente llama a esta función cuando el parámetro PREPROCESS\_FUNCTION está en el [archivo .vsz de control del proyecto](../ide/dot-vsz-file-project-control.md) y comprueba si el [Visual C\+\+ Code Model](http://msdn.microsoft.com/es-es/dd6452c2-1054-44a1-b0eb-639a94a1216b) está disponible.  Si el modelo de código no está disponible, la función informará de un error y devolverá **false**.|  
|[CanAddClass](../ide/canaddclass.md)|El asistente llama a esta función cuando el parámetro PREPROCESS\_FUNCTION está en el archivo .vsz de control del proyecto.<br /><br /> Comprueba si está disponible el objeto del modelo de código de Visual C\+\+.  Si el modelo de código no está disponible, la función informará de un error y devolverá **false**.|  
|[CanAddMFCClass](../ide/canaddmfcclass.md)|El asistente llama a esta función para comprobar si el proyecto es compatible con el asistente para código que va a ejecutarse \(es decir, si puede aceptar una clase MFC\).<br /><br /> El asistente llama a esta función cuando el parámetro PREPROCESS\_FUNCTION está en el archivo .vsz de control del proyecto y comprueba si el objeto del modelo de código de Visual C\+\+ está disponible.  Si el modelo de código no está disponible, la función informará de un error y devolverá **false**.|  
|[CanAddNonAttributed](../ide/canaddnonattributed.md)|Indica si el proyecto es compatible con objetos ATL con y sin atributos.|  
|[CanUseFileName](../ide/canusefilename.md)|Comprueba si existe un archivo.  De existir, el asistente le pedirá al usuario que combine el código que va a agregarse en el archivo existente.|  
|[ConvertProjectToAttributed](../ide/convertprojecttoattributed.md)|Convierte un proyecto ATL en un proyecto con atributos.|  
|[CreateInfFile](../ide/createinffile.md)|Crea el archivo Templates.inf.|  
|[CreateProject](../ide/createproject.md)|Crea un proyecto de C\+\+.|  
|[CreateSafeName](../ide/createsafename.md)|Genera un nombre descriptivo de C\+\+.|  
|[DeleteFile](../ide/deletefile.md)|Elimina el archivo especificado.|  
|[DoesIncludeExist](../ide/doesincludeexist.md)|Indica si existe una instrucción `#include` dentro de un archivo.|  
|[GetCodeForDllCanUnloadNow](../ide/getcodefordllcanunloadnow.md)|Recupera el código necesario para descargar la DLL.|  
|[GetCodeForDllGetClassObject](../ide/getcodefordllgetclassobject.md)|Recupera el código del objeto de clase de DLL.|  
|[GetCodeForDllRegisterServer](../ide/getcodefordllregisterserver.md)|Recupera el código para registrar un servidor.|  
|[GetCodeForDllUnregisterServer](../ide/getcodefordllunregisterserver.md)|Recupera el código para anular el registro de un servidor.|  
|[GetCodeForExitInstance](../ide/getcodeforexitinstance.md)|Función auxiliar para obtener el texto para `ExitInstance`.|  
|[GetCodeForInitInstance](../ide/getcodeforinitinstance.md)|Función auxiliar para obtener el texto para [InitInstance](../Topic/CWinApp::InitInstance.md).|  
|[GetExportPragmas](../ide/getexportpragmas.md)|Recupera las directivas pragma para exportar funciones.|  
|[GetInterfaceClasses](../ide/getinterfaceclasses.md)|Devuelve el objeto `VCCodeClass` asociado a una interfaz.|  
|[GetInterfaceType](../ide/getinterfacetype.md)|Devuelve el tipo de interfaz \(por ejemplo, personalizada, dual, dispinterface, oleautomation\).|  
|[GetMaxID](../ide/getmaxid.md)|Devuelve el *identificador de envío* \(`dispid`\) más alto de los miembros de la interfaz, así como todas sus bases.|  
|[GetMemberfunction](../ide/getmemberfunction.md)|Devuelve un objeto de función basado en el nombre especificado.|  
|[GetProjectFile](../ide/getprojectfile.md)|Devuelve el nombre de archivo de los tipos de archivo por proyecto \(.rc, .idl, etc.\).|  
|[GetProjectPath](../ide/getprojectpath.md)|Devuelve la ruta de acceso del directorio del proyecto.|  
|[GetRuntimeErrorDesc](../ide/getruntimeerrordesc.md)|Devuelve una descripción del tipo de excepción.|  
|[GetUniqueFileName](../ide/getuniquefilename.md)|Devuelve un nombre de archivo único.|  
|[IncludeCodeElementDeclaration](../ide/includecodeelementdeclaration.md)|Agrega la instrucción de inclusión a `strInFile`, incluyendo el encabezado donde se implementa `strCodeElemName` \(si es que está en el proyecto\).|  
|[InsertIntoFunction](../ide/insertintofunction.md)|Función auxiliar llamada en `AddATLSupportToProject` para insertar código en `InitInstance`.|  
|[IsATLProject](../ide/isatlproject.md)|Indica si el proyecto se basa en ATL.|  
|[IsAttributedProject](../ide/isattributedproject.md)|Indica si un proyecto tiene atributos.|  
|[IsMFCProject](../ide/ismfcproject.md)|Comprueba si un proyecto se basa en MFC.|  
|[LineBeginsWith](../ide/linebeginswith.md)|Función auxiliar llamada en `InsertIntoFunction` para determinar si una línea empieza con una cadena concreta.|  
|[OffsetToLineNumber](../ide/offsettolinenumber.md)|Busca el número de línea de una posición determinada dentro del cuerpo de una función.|  
|[OnWizFinish](../ide/onwizfinish.md)|Se llama a esta función desde el script HTML del asistente cuando el usuario hace clic en **Finalizar**.  Llama al método **Finish** del control del asistente.|  
|[RenderAddTemplate](../ide/renderaddtemplate.md)|Representa un archivo de plantilla y, opcionalmente, lo agrega al proyecto.|  
|[SetCommonPchSettings](../ide/setcommonpchsettings.md)|Establece el encabezado precompilado del proyecto.|  
|[SetErrorInfo](../ide/seterrorinfo.md)|Proporciona información sobre errores.|  
|[SetFilters](../ide/setfilters.md)|Agrega filtros de origen, inclusión y recursos para las carpetas del proyecto.|  
|[SetMergeProxySymbol](../ide/setmergeproxysymbol.md)|Función a la que llama el asistente para agregar, cuando sea necesario, el símbolo \_MERGE\_PROXYSTUB.|  
|[SetNoPchSettings](../ide/setnopchsettings.md)|Establece las propiedades de configuración del proyecto cuando no se utiliza ningún encabezado precompilado.|  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)