

from ncclient import manager
host = '10.171.182.145'
cisco_manager = manager.connect (host= host, port=22, username= 'csco-se', password='5GSupport@ATT', hostkey_verify=False, device_params={'name': 'iosxr'}, timeout = 5000, allow_agent=False, look_for_keys=False)

interfacecfg = """
 <config xmlns:xc="urn:ietf:params:xml:ns:netconf:base:1.0">
  <interface-configurations xmlns="http://cisco.com/ns/yang/Cisco-IOS-XR-ifmgr-cfg"  xc:operation="merge">
   <interface-configuration>
    <active>act</active>
    <interface-name>Loopback99</interface-name>
    <interface-virtual/>
    <ipv4-network xmlns="http://cisco.com/ns/yang/Cisco-IOS-XR-ipv4-io-cfg">
     <addresses>
      <primary>
       <address>10.99.1.99</address>
       <netmask>255.255.255.255</netmask>
      </primary>
     </addresses>
    </ipv4-network>
   </interface-configuration>
  </interface-configurations>
 </config>
"""

data = cisco_manager.edit_config ( interfacecfg, target='candidate')
print (data)
reply = cisco_manager.commit()
cisco_manager.close_session()
