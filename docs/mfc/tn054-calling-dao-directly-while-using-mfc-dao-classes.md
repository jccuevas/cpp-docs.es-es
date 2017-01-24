---
title: "TN054: Llamar a DAO directamente mientras se usan clases DAO de MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.dao"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO (objetos de acceso a datos), y MFC"
  - "DAO (objetos de acceso a datos), llamar directamente"
  - "DAO (objetos de acceso a datos), seguridad"
  - "MFC [C++], DAO y"
  - "contraseñas [C++], llamar DAO"
  - "seguridad [MFC]"
  - "seguridad [MFC], DAO"
  - "TN054"
ms.assetid: f7de7d85-8d6c-4426-aa05-2e617c0da957
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN054: Llamar a DAO directamente mientras se usan clases DAO de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  A partir de Visual C\+\+ .NET, el entorno y los asistentes de Visual C\+\+ ya no admiten DAO \(aunque las clases DAO están incluidas y todavía puede utilizarlas\).  Microsoft recomienda utilizar [Plantillas OLE DB](../data/oledb/ole-db-templates.md) o [ODBC y MFC](../data/odbc/odbc-and-mfc.md) para nuevos proyectos.  Sólo debería utilizar DAO para mantener las aplicaciones existentes.  
  
 Al utilizar las clases de base de datos DAO de MFC, puede haber situaciones donde es necesario utilizar DAO directamente.  Normalmente, no será el caso, pero MFC ha proporcionado a algunos mecanismos auxiliares para facilitar la creación de las llamadas directas de DAO simples al combinar el uso de las clases MFC con llamadas directas de DAO.  Realizar llamadas directas a DAO a los métodos de un objeto MFC\- administrado DAO debe requerir sólo algunas líneas de código.  Si necesita crear y utilizar los objetos DAO que no son administrados por MFC, tendrá que hacer algo más trabajo realmente llamando a **Versión** en el objeto.  Esta nota técnica explica cuándo puede resultar conveniente llamar a DAO directamente, lo que pueden hacer que las aplicaciones auxiliares de MFC para ayudarle, y cómo utilizar las interfaces de DAO OLE.  Finalmente, esta nota proporciona algunas funciones de ejemplo que muestran cómo llamar directamente a objetos DAO directamente para las características de seguridad DAO.  
  
## Cuándo realizar llamadas Directas de DAO  
 Los escenarios más comunes para realizar llamadas directas a DAO se producen cuando las colecciones deben actualizarse o cuando se implementa las características no contenidas en MFC.  La característica más importante no expuesta por MFC es seguridad.  Si desea implementar características de seguridad, deberá utilizar los objetos de los usuarios y grupos de DAO directamente.  Además de seguridad, sólo hay otras características de DAO no admitidas por MFC.  Estos incluyen la clonación de conjunto de registros y las características de replicación de bases de datos así como algunas últimas adiciones a DAO.  
  
## Información general sobre Brief DAO y de MFC  
 El ajuste de MFC DAO crea utilizando DAO más fácil administrar muchos de los detalles de modo que no tiene que preocuparse de las pequeñas cosas.  Esto incluye la inicialización de OLE, la creación y la administración de los objetos DAO \(sobre todo los objetos collection\), comprobación de errores, y proporcionar una interfaz fuertemente tipada, más simple \(sin **VARIANT** o argumentos de `BSTR` \).  Puede realizar llamadas directas de DAO y todavía aprovechar estas características.  Todo el código debe hacer es llamar a **Versión** para cualquier objeto creado por llamadas directas de DAO y no modificar punteros cualquiera de la interfaz que MFC puede confiar en internamente.  Por ejemplo, no modifique el miembro de **m\_pDAORecordset** de un objeto abierto de `CDaoRecordset` a menos que conozca *todas las* ramificaciones internas.  Puede, sin embargo, usar la interfaz de **m\_pDAORecordset** para llamar directamente a objetos DAO directamente para obtener la colección de campos.  En este caso no modificarían al miembro de **m\_pDAORecordset** .  Tiene que llamar simplemente **Versión** en el objeto de colección de campos cuando termine con el objeto.  
  
## Descripción de las aplicaciones auxiliares para realizar llamadas Easier DAO  
 Las aplicaciones auxiliares proporcionadas para crear llamar directamente a objetos DAO más fácil son las mismas aplicaciones auxiliares que se usan internamente en las clases de base de datos DAO de MFC.  Utilizan estas aplicaciones auxiliares para comprobar los códigos devueltos al crear una llamada directa de DAO, salida de registro de depuración, comprobando los errores esperados, y producir excepciones adecuadas en caso necesario.  Hay dos funciones subyacentes auxiliar y cuatro macros que se asignan a una de estas dos aplicaciones auxiliares.  La mejor explicación sería leer simplemente el código.  Vea **DAO\_CHECK**, **DAO\_CHECK\_ERROR**, **DAO\_CHECK\_MEM**, y **DAO\_TRACE** en AFXDAO.H para ver las macros y, vea **AfxDaoCheck** y **AfxDaoTrace** en DAOCORE.CPP.  
  
## Mediante las interfaces de DAO OLE  
 Las interfaces VIEJAS para cada objeto en la jerarquía de objetos DAO se definen en el archivo de encabezado DBDAOINT.H, que se encuentra en el directorio de \\include de Files\\Microsoft Visual Studio .NET 2003\\V C7 del \\Program.  Estas interfaces proporcionan métodos que permiten manipular la jerarquía completa de DAO.  
  
 Para muchos de los métodos de las interfaces de DAO, deberá manipular un objeto de `BSTR` \(una cadena longitud\- fija utilizada en la automatización OLE\).  El objeto de `BSTR` se encapsula normalmente dentro del tipo de datos de **VARIANT** .  La clase MFC `COleVariant` propio hereda del tipo de datos de **VARIANT** .  Dependiendo de si se compila el proyecto para ANSI o Unicode, las interfaces de DAO devolverán ANSI o s Unicode `BSTR`.  Dos macros, **V\_BSTR** y **V\_BSTRT**, son útiles para garantizar que la interfaz de DAO obtiene `BSTR` del tipo esperado.  
  
 **V\_BSTR** extraerá al miembro de **bstrVal** de `COleVariant`.  Esta macro se utiliza normalmente cuando necesita pasar el contenido de `COleVariant` a un método de una interfaz de DAO.  El fragmento de código siguiente muestra declaraciones y el uso real para dos métodos de la interfaz de DAO DAOUser que se aprovechen de la macro de **V\_BSTR** :  
  
```  
COleVariant varOldName;  
COleVariant varNewName( _T("NewUser"), VT_BSTRT );  
  
// Code to assign pUser to a valid value omitted  
DAOUser *pUser = NULL;  
  
// These method declarations were taken from DBDAOINT.H  
// STDMETHOD(get_Name) (THIS_ BSTR FAR* pbstr) PURE;  
// STDMETHOD(put_Name) (THIS_ BSTR bstr) PURE;  
  
DAO_CHECK( pUser->get_Name( &V_BSTR ( &varOldName ) ));  
DAO_CHECK( pUser->put_Name( V_BSTR ( &varNewName ) ));  
```  
  
 Observe que el argumento de `VT_BSTRT` especificado en el constructor de `COleVariant` anterior garantiza que habrá ANSI `BSTR` en `COleVariant` si se compila una versión ANSI de la aplicación y Unicode `BSTR` para una versión Unicode de la aplicación.  Esto es lo que espera DAO.  
  
 La otra macro, **V\_BSTRT**, extraerá ANSI o miembro Unicode **bstrVal** de `COleVariant` según el tipo de compilación \(ANSI o Unicode\).  El código siguiente se muestra cómo extraer el valor de `BSTR` de `COleVariant` en `CString`:  
  
```  
COleVariant varName( _T( "MyName" ), VT_BSTRT );  
CString str = V_BSTRT( &varName );  
```  
  
 La macro de **V\_BSTRT** , junto con otras técnicas de abrir otros tipos que se almacenan en `COleVariant`, se muestra en el ejemplo de DAOVIEW.  Específicamente, esta conversión se realiza en el método de **CCrack::strVARIANT** .  Este método, cuando sea posible, convierte el valor de `COleVariant` a una instancia de `CString`.  
  
## Ejemplo simple de una llamada de Direct a DAO  
 Los escenarios pueden surgir cuando es necesario actualizar los objetos collection subyacentes de DAO.  Normalmente, esto no debería ser necesario, pero es un procedimiento simple si es necesario.  Un ejemplo de cuándo una colección podría necesitar actualizar es al trabajar en un entorno multiusuario con varios usuarios que crean nuevos tabledefs.  En este caso la colección de los tabledefs podría quedar obsoleta.  Para actualizar la colección, sólo tiene que llamar al método de **Actuali&&zar** del objeto collection set y comprobación de errores:  
  
```  
DAO_CHECK( pMyDaoDatabase->  
    m_pDAOTableDefs->Refresh( ) );  
```  
  
 Observe que todas las interfaces del objeto de colección DAO están actualmente detalles de implementación indocumentados de las clases de base de datos DAO de MFC.  
  
## Utilizando DAO Directamente para las características de seguridad DAO  
 Las clases de base de datos DAO de MFC no ajustan las características de seguridad DAO.  Debe llamar a métodos de interfaces de DAO para utilizar algunas características de seguridad DAO.  La siguiente función establece la base de datos del sistema y después cambia la contraseña del usuario.  Esta función se llama otras tres funciones, definidos posteriormente.  
  
```  
void ChangeUserPassword( )  
{  
   // Specify path to the Microsoft Access  
   // system database  
   CString strSystemDB =   
     _T( "c:\\Program Files\\MSOffice\\access\\System.mdw" );  
  
   // Set system database before MFC initilizes DAO  
   // NOTE: An MFC module uses only one instance   
   // of a DAO database engine object. If you have   
   // called a DAO object in your application prior   
   // to calling the function below, you must call   
   // AfxDaoTerm to destroy the existing database   
   // engine object. Otherwise, the database engine   
   // object already in use will be reused, and setting  
   // a system datbase will have no effect.  
   //  
   // If you have used a DAO object prior to calling   
   // this function it is important that DAO be   
   // terminated with AfxDaoTerm since an MFC  
   // module only gets one copy of the database engine   
   // and that engine will be reused if it hasn't been   
   // terminated. In other words, if you do not call   
   // AfxDaoTerm and there is currently a database   
   // initialized, setting the system database will   
   // have no affect.  
  
   SetSystemDB( strSystemDB );  
  
   // User name and password manually added  
   // by using Microsoft Access  
   CString strUserName = _T( "NewUser" );  
   CString strOldPassword = _T( "Password" );  
   CString strNewPassword = _T( "NewPassword" );  
  
   // Set default user so that MFC will be able  
   // to log in by default using the user name and   
   // password from the system database  
   SetDefaultUser( strUserName, strOldPassword );  
  
   // Change the password. You should be able to  
   // call this function from anywhere in your   
   // MFC application  
   ChangePassword( strUserName, strOldPassword,   
                   strNewPassword );  
  
   .  
   .  
   .  
  
}  
```  
  
 Los cuatro ejemplos siguientes muestran cómo:  
  
-   Establezca la base de datos del sistema DAO \(archivo de .MDW\).  
  
-   Establezca el usuario y la contraseña predeterminados.  
  
-   Cambie la contraseña de un usuario.  
  
-   Cambie la contraseña de un archivo de .MDB.  
  
### Establecer la base de datos del sistema  
 A continuación se muestra una función de ejemplo para establecer la base de datos del sistema que se utilizará en una aplicación.  Esta función debe llamar antes de que se haga cualquier otra llamada DAO.  
  
```  
// Set the system database that the   
// DAO database engine will use  
  
void SetSystemDB( CString & strSystemMDB )  
{  
   COleVariant varSystemDB( strSystemMDB, VT_BSTRT );  
  
   // Initialize DAO for MFC  
   AfxDaoInit( );  
   DAODBEngine* pDBEngine = AfxDaoGetEngine( );  
  
   ASSERT( pDBEngine != NULL );  
  
   // Call put_SystemDB method to set the   
   // system database for DAO engine  
   DAO_CHECK( pDBEngine->put_SystemDB( varSystemDB.bstrVal ) );  
}  
```  
  
### Establecer el usuario y la contraseña predeterminados  
 Para establecer el usuario y la contraseña predeterminados para una base de datos del sistema, utilice la siguiente función:  
  
```  
void SetDefaultUser(CString & strUserName, CString & strPassword)  
{  
  COleVariant varUserName( strUserName, VT_BSTRT );  
  COleVariant varPassword( strPassword, VT_BSTRT );  
  
  DAODBEngine* pDBEngine = AfxDaoGetEngine( );  
  ASSERT( pDBEngine != NULL );  
  
  // Set default user:  
  DAO_CHECK( pDBEngine->put_DefaultUser( varUserName.bstrVal ) );  
  
  // Set default password:  
  DAO_CHECK( pDBEngine->put_DefaultPassword( varPassword.bstrVal ) );  
}  
```  
  
### Cambiar una contraseña de usuario  
 Para cambiar la contraseña de un usuario, utilice la siguiente función:  
  
```  
void ChangePassword( CString &strUserName,   
                     CString &strOldPassword,   
                     CString &strNewPassword )  
{  
   // Create (open) a workspace  
   CDaoWorkspace wsp;  
   CString strWspName = _T( "Temp Workspace" );  
  
   wsp.Create( strWspName, strUserName,  
               strOldPassword );  
   wsp.Append( );  
  
   // Determine how many objects there are  
   // in the Users collection  
   short nUserCount;  
   short nCurrentUser;  
   DAOUser *pUser  = NULL;  
   DAOUsers *pUsers = NULL;  
  
   // Side-effect is implicit OLE AddRef( )   
   // on DAOUser object:  
   DAO_CHECK( wsp.m_pDAOWorkspace->get_Users( &pUsers ) );  
  
   // Side-effect is implicit OLE AddRef( )   
   // on DAOUsers object  
    DAO_CHECK( pUsers->get_Count( &nUserCount ) );  
  
   // Traverse through the list of users   
   // and change password for the userid  
   // used to create/open the workspace  
   for( nCurrentUser = 0; nCurrentUser < nUserCount;  
        nCurrentUser++ )  
   {  
       COleVariant varIndex( nCurrentUser, VT_I2 );  
       COleVariant varName;  
  
       // Retrieve information for user nCurrentUser  
       DAO_CHECK( pUsers->get_Item( varIndex, &pUser ) );  
  
       // Retrieve name for user nCurrentUser  
       DAO_CHECK( pUser->get_Name( &V_BSTR( &varName ) ) );  
  
       CString strTemp = V_BSTRT( &varName );  
  
       // If there is a match, change the password  
       if( strTemp == strUserName )  
       {  
           COleVariant varOldPwd( strOldPassword,   
                                  VT_BSTRT );  
           COleVariant varNewPwd( strNewPassword,   
                                  VT_BSTRT );  
  
           DAO_CHECK( pUser->NewPassword( V_BSTR( &varOldPwd ),  
                      V_BSTR( &varNewPwd ) ) );  
  
           TRACE( "\t Password is changed\n" );  
       }  
   }  
  
   // Clean up: decrement the usage count  
   // on the OLE objects  
   pUser->Release( );  
   pUsers->Release( );  
  
   wsp.Close( );  
}  
```  
  
### Cambiar la contraseña de un archivo de .MDB  
 Para cambiar la contraseña de un archivo de .MDB, utilice la siguiente función:  
  
```  
void SetDBPassword( LPCTSTR pDB, LPCTSTR pszOldPassword, LPCTSTR pszNewPassword )  
{  
   CDaoDatabase db;  
   CString strConnect( _T( ";pwd=" ) );  
  
   // the database must be opened as exclusive  
   // to set a password  
   db.Open( pDB, TRUE, FALSE,   
            strConnect + pszOldPassword );  
  
   COleVariant NewPassword( pszNewPassword, VT_BSTRT ),  
               OldPassword( pszOldPassword, VT_BSTRT );  
  
   DAO_CHECK( db.m_pDAODatabase->NewPassword( V_BSTR( &OldPassword ),  
              V_BSTR( &NewPassword ) ) );  
  
   db.Close();  
}  
```  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)