# Eth_Avax_Module2_Final

**Aim of the project**

Integrating a smart contract with the frontend application.

**Code of the program**

     pragma solidity ^0.5.11;

    contract ElectionVoting{

    struct Candidate{
        uint id;
        string name;
        uint voteCount;

    }

    mapping (uint => Candidate) public candidates;
    uint public candidatecount;
    mapping (address => bool) public voter;

    event eventVote(
        uint indexed _candidateid
    );

    function Election ()public{
        addCandidate("Alice");
        addCandidate("Bob");
    }

    function addCandidate (string memory _name) private{
        candidatecount ++;
        candidates[candidatecount] = Candidate(candidatecount, _name, 0);
    }

    function vote(uint _candidateid) public {

        require(!voter[msg.sender]);

        require(_candidateid > 0 && _candidateid <= candidatecount);

        voter[msg.sender] = true;

        candidates[_candidateid].voteCount ++;

        emit eventVote(_candidateid);
    }

    }

**Functionality of the code**

1. pragma solidity ^0.5.11 specifies the version of Solidity.

2. struct Candidate defines a candidate with three properties: id, name, and voteCount.

3. mapping (uint => Candidate) public candidates associates each candidate's id (uint) with the corresponding Candidate struct. The public keyword allows other contracts or users to access the candidate information.

4. uint public candidatecount keeps track of the total number of candidates added to the election.

5. mapping (address => bool) public voter keeps track of whether an address has voted or not. 

6. event eventVote(uint indexed _candidateid) is an event that will be emitted whenever a user votes for a candidate. The event includes the candidate's id.

7. function Election() public is a constructor function which is executed only once when the contract is deployed. It automatically adds two candidates, "Alice" and "Bob," to the election.

8. function addCandidate(string memory _name) private is used to add a new candidate to the election. It takes the candidate's name as its parameter and creates a new Candidate struct with the next candidate id and the given name. The candidate count is incremented, and the candidate is added to the candidates mapping.

9. function vote(uint _candidateid) public is used for casting votes. It takes the candidate id as its parameter and allows a user to vote for a specific candidate. If the conditions are met, the user's address is marked as having voted, and the vote count for the chosen candidate is incremented. The eventVote event is then emitted to let voters know about the vote.

**Functionality of the code**

1. Install the "npm i" to install the project dependencies.

2. Then type install "npm install truffle -g" to install truffle.

3. Then type "npm install web3" to install features of the web interface.

4. Then type "truffle migrate --network development --reset" to compile and migrate the contract to the network.

5. Then at last type the command "npm run dev " to run the application on localhost.

**Author**
Sehajpreet Kaur (21BCS4518@cuchd.in)
