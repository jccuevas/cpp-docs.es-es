---
title: "Controles ActiveX MFC: Distribuir controles ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetWindowsDirectory"
  - "GetSystemDirectory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "distribuir controles ActiveX en MFC"
  - "GetProcAddress (método), registrar controles ActiveX"
  - "GetSystemDirectory (método)"
  - "GetWindowsDirectory (método)"
  - "instalar controles ActiveX"
  - "LoadLibrary (método), registrar controles ActiveX"
  - "controles ActiveX en MFC, versiones ANSI o Unicode"
  - "controles ActiveX en MFC, distribuir"
  - "controles ActiveX en MFC, instalar"
  - "controles ActiveX en MFC, registrar"
  - "MFC40.DLL"
  - "MFC40U.DLL"
  - "MSVCRT40.dll"
  - "OLEPRO32.DLL"
  - "archivos redistribuibles, controles ActiveX en MFC"
  - "registrar controles ActiveX"
  - "registrar controles"
  - "Registro, registrar controles"
  - "RegSvr32.exe"
ms.assetid: cd70ac9b-f613-4879-9e81-6381fdfda2a1
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Controles ActiveX MFC: Distribuir controles ActiveX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se abordan varios problemas relacionados con redistribuir controles ActiveX:  
  
-   [ANSI o versiones de Control Unicode](#_core_ansi_or_unicode_control_versions)  
  
-   [Instalar los Controles ActiveX y DLL redistribuibles](#_core_installing_activex_controls_and_redistributable_dlls)  
  
-   [Registrar Controles](#_core_registering_controls)  
  
    > [!NOTE]
    >  Para obtener más información sobre cómo redistribuir controles ActiveX, vea [Redistribuir Controles](../data/ado-rdo/redistributing-controls.md).  
  
##  <a name="_core_ansi_or_unicode_control_versions"></a> ANSI o versiones de Control Unicode  
 Debe decidir si distribuir una versión ANSI o Unicode del control, o ambos.  Esta decisión se basa en los factores de portabilidad inherentes a ANSI y los juegos de caracteres Unicode.  
  
 Los controles de ANSI, que funcionan en todos los sistemas operativos de Win32, permiten portabilidad máxima entre los sistemas operativos diferentes de Win32.  Los controles de Unicode funcionan únicamente en Windows NT \(versión 3.51 o posterior\), pero no en Windows 95 o Windows 98.  Si la portabilidad es preocuparse primarios, los controles de ANSI de la nave.  Si los controles sólo se ejecutan en Windows NT, puede enviar los controles Unicode.  También podría decidir para enviar y tener la aplicación instale la versión más adecuada para el sistema operativo del usuario.  
  
##  <a name="_core_installing_activex_controls_and_redistributable_dlls"></a> Instalar los Controles ActiveX y DLL redistribuibles  
 El programa de instalación que se proporcionan controles ActiveX debe crear un subdirectorio especial del directorio Windows e instalar los archivos de .OCX de los controles en él.  
  
> [!NOTE]
>  Utilice Windows **GetWindowsDirectory** API en el programa de instalación para obtener el nombre del directorio de Windows.  Quizá desee derivar el nombre del subdirectorio del nombre de la compañía o del producto.  
  
 El programa de instalación debe instalar archivos redistribuibles necesarios de DLL en el directorio system de Windows.  Si alguno de los archivos DLL ya están presentes en el equipo del usuario, el programa de instalación debe comparar sus versiones con las versiones que está instalando.  Vuelva a instalar un archivo si el número de versión es más alto que el archivo instalado.  
  
 Dado que los controles ActiveX se pueden utilizar en aplicaciones contenedoras VIEJAS, no hay necesidad de distribuir el conjunto completo de DLL OLE con controles.  Puede suponer que la aplicación que contiene \(o el sistema operativo propio\) tiene las DLL OLE estándar instaladas.  
  
##  <a name="_core_registering_controls"></a> Registrar Controles  
 Antes de que un control puede utilizar, las entradas adecuadas se deben crear para él en la base de datos del registro de Windows.  Algunos contenedores de controles ActiveX proporcionan un elemento de menú de los usuarios a los nuevos controles de registro, pero esta característica puede no estar disponible en todos los contenedores.  Por consiguiente, puede que el programa de instalación para registrar los controles cuando se instalan.  
  
 Si lo prefiere, puede escribir el programa de instalación para registrar el control directamente en su lugar.  
  
 Utilice la API de Windows **LoadLibrary** para cargar el control DLL.  A continuación, utilice **GetProcAddress** de obtener la dirección de la función de “DllRegisterServer”.  Por último, llame a la función de `DllRegisterServer` .  El siguiente ejemplo de código muestra un método posible, donde `hLib` almacena el identificador de biblioteca de controles, y `lpDllEntryPoint` almacena la dirección de la función de “DllRegisterServer”.  
  
 [!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/CPP/mfc-activex-controls-distributing-activex-controls_1.cpp)]  
  
 La ventaja de registrar el control directamente es que no es necesario invocar y cargar un proceso independiente \(concretamente, REGSVR32\), reduce tiempo de instalación.  Además, dado que el registro es un proceso interno, el programa de instalación puede controlar errores y situaciones imprevistas mejor que puede un proceso externo.  
  
> [!NOTE]
>  Antes de que el programa de instalación instale un control ActiveX, debe llamar a **OleInitialize**.  Cuando finalice el programa de instalación, llame a **OleUnitialize**.  Esto garantiza que los archivos DLL del sistema OLE están en estado adecuada para registrar un control ActiveX.  
  
 Debe registrar MFCx0.DLL.  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)