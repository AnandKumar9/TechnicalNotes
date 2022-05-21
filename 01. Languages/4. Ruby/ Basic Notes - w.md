Running a Ruby script has the same usual process as running other scripts (say Python). Save the file with .rb extension and then run it from command line with ruby command.

###### Modifying strings -

str1 = "ABCXYZ"
str1.slice! "XYZ"       # This actually removes the substring from passed string itself

str2 = "Hey " + str1 + "there."    # String concatenation


Type conversion, etc. -

someFloat.to_s            # Converts to string
someString.to_f           # Converts to float
someFloat.round(2)        # Round a float to 2 decimal points


Hashes -

Hash is nothing but a dictionary. They are represented in this syntax.
{:key1=>1, :key2=>2}

hash1 = Hash.new          # Creating a new Hash


Array operations -

sum = newCoverageData.xpath("//class").reduce(0) { |sum, element| sum + element["line-rate"].to_f}      # reduce
x = newCoverageData.xpath("//class").count      # count


Parsing XML -

Nokogiri is one of the libraries that can be used for it.

require 'nokogiri'

xmlData = Nokogiri::XML(File.read(slatherResultPath))    # The xml file path specified here. probably even an XML string can be specified.
elementsInXML = slatherResultData.xpath("//class")

parsedXML = elementsInXML.each do |element|              # elementsInXML is an array
  attribute1 = element["line-rate"]
  attribute2 = element["name"]
end

File operations -

Check if a file exists and rename it.

if File.exist?(locationFile)
  File.rename(locationFile, locationExistingFileRenamed)
end


Misc. -

Accessing environment variables - ENV['envVariable1']
