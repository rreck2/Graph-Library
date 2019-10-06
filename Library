GRAPH = {} 
directed = False;
weighted = False;

def addVertex(s, d = None, w = '0'):
    if(s not in GRAPH):
        GRAPH[s] = []
    list = GRAPH[s]
    if(d != None) and d != '':
        list.append([d,w])
    GRAPH[s] = list

def printGraph():
    for source in GRAPH:
        row = source + " : ";
        for dest in GRAPH[source]:
            if(weighted):
                row = row + "(" + dest[0] + ", " + dest[1] + ")"
            else:
                row = row + dest[0]
            if(GRAPH[source].index(dest) != len(GRAPH[source])-1):
                row = row + ", " 
        print(row);

def readFileAndPrint():
    global directed, weighted # Refer to Global Variable
    file = open("graph.txt", "r")
    config = file.readline() # Read first line of file to get the graph type
    config = config.strip('\n')
    config = config.split(" ")
    if(config[0] == "directed"):
        directed = True
    if(config[1] == "weighted"):
        weighted = True

    for line in file: # read rest of the file line by line
        line = line.strip('\n') # eliminate end of line character
        temp = line.split("=")
        if(len(temp) == 3):
            addVertex(temp[0], temp[1], temp[2])
            if(directed == False): # if undirected graph, make entry for destination to source as well
                addVertex(temp[1], temp[0], temp[2])
        elif(len(temp) == 2):
            addVertex(temp[0], temp[1])
            if(directed == False and temp[1] != ''):
                addVertex(temp[1], temp[0])
        elif(len(temp) == 1):
            addVertex(temp[0])

    printGraph();


readFileAndPrint();
