``` xml

<?xml version="1.0"?>
<pecan>
  
    <info>
      <notes></notes>
      <username>ecalder1</username>
      <date>2022/08/27 18:33:38 +0000</date>
    </info>
  
    <outdir>/data/workflows/PEcAn_99000000012</outdir>
    
    <!-- db config -->
    <database>
      <bety>
        <user>bety</user>
        <password>bety</password>
        <host>postgres</host>
        <port>5432</port>
        <dbname>bety</dbname>
        <driver>PostgreSQL</driver>
        <write>true</write>
      </bety>
      <dbfiles>/data/dbfiles</dbfiles>
    </database>
  
    <!-- Plant functional type -->
    <pfts>
      <pft>
        <name>temperate.deciduous</name> 
      </pft>
    </pfts>
  
    <!-- Meta Analysis config -->
    <meta.analysis>
      <iter>3000</iter>
      <random.effects>
        <on>FALSE</on>
        <use_ghs>TRUE</use_ghs>
      </random.effects>
    </meta.analysis>
  
    <!-- Ensemble config -->
    <ensemble>
      <size>4</size>
      <variable>NPP</variable>
      <start.year>2004</start.year>
      <end.year>2004</end.year>
      
      <samplingspace>
    
        <parameters>
            <method>uniform</method>
        </parameters>
   
        <met>
          <method>sampling</method>
 	      </met>
      </samplingspace>
  </ensemble>
  
  <model>
    <id>1000000014</id>
  </model>
  <workflow>
    <id>99000000011</id>
  </workflow>
  <run>
    <site>
      <id>772</id>
      <met.start>2002-01-01 00:00:00</met.start>
      <met.end>2005-12-31 00:00:00</met.end>
    </site>
    <inputs>
      <met>
        <id>5000000005</id>
      </met>
    </inputs>
    <start.date>2004/01/01</start.date>
    <end.date>2004/12/31</end.date>
  </run>
  <host>
    <name>localhost</name>
    <rabbitmq>
      <uri>amqp://guest:guest@rabbitmq/%2F</uri>
      <queue>SIPNET_r136</queue>
    </rabbitmq>
  </host>

</pecan>



```
